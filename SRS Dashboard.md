```dataviewjs
const today = window.moment().startOf('day');

// Fetch all pages tagged with #review
const allPages = dv.pages('#review');

// 1. Filter and sort pages that are due today or overdue (or are completely new)
const duePages = allPages.where(p => {
    if (!p.sr_next) return true;
    const nextDate = window.moment(p.sr_next, 'YYYY-MM-DD').startOf('day');
    return nextDate.isSameOrBefore(today);
}).sort(p => {
    if (!p.sr_next) return 999; 
    const nextDate = window.moment(p.sr_next, 'YYYY-MM-DD').startOf('day');
    return today.diff(nextDate, 'days');
}, 'desc');

// 2. Filter and sort pages scheduled for future dates
const upcomingPages = allPages.where(p => {
    if (!p.sr_next) return false;
    const nextDate = window.moment(p.sr_next, 'YYYY-MM-DD').startOf('day');
    return nextDate.isAfter(today);
}).sort(p => {
    const nextDate = window.moment(p.sr_next, 'YYYY-MM-DD').startOf('day');
    return nextDate.diff(today, 'days');
}, 'asc');

// --- RENDER DUE SECTION ---
dv.header(3, "📅 Due & Overdue Reviews");
if (duePages.length === 0) {
    dv.paragraph("🎉 **All caught up! No custom reviews due today.**");
} else {
    const rows = [];
    
    duePages.forEach(p => {
        const currentInterval = p.sr_interval || 1;
        const currentEase = p.sr_ease || 2.5;
        
        // Determine Type Icon
        const typeIcon = p.type === 'practical' ? "💻 Practical" : "🧠 Theory";
        
        // Calculate Overdue Status
        let overdueText = "✨ New";
        if (p.sr_next) {
            const nextDate = window.moment(p.sr_next, 'YYYY-MM-DD').startOf('day');
            const diff = today.diff(nextDate, 'days');
            overdueText = diff === 0 ? "📅 Due Today" : `⚠️ ${diff}d Overdue`;
        }

        // Generate Action Buttons Row
        const actionContainer = document.createElement('div');
        actionContainer.style.display = "flex";
        actionContainer.style.gap = "6px";

        const disableAll = () => {
            btnForgot.disabled = true;
            btnHard.disabled = true;
            btnGood.disabled = true;
        };

        // 🔴 FORGOT
        const btnForgot = document.createElement('button');
        btnForgot.innerText = "🔴 Forgot";
        btnForgot.onclick = async () => {
            await updateSRData(p.file.path, 1, currentEase);
            btnForgot.innerText = "Reset 🔄";
            disableAll();
        };

        // 🟡 HARD (1.2x modifier)
        const btnHard = document.createElement('button');
        btnHard.innerText = "🟡 Hard";
        btnHard.onclick = async () => {
            const nextInterval = Math.max(1, Math.round(currentInterval * 1.2));
            await updateSRData(p.file.path, nextInterval, currentEase);
            btnHard.innerText = "Saved 🩹";
            disableAll();
        };

        // 🟢 GOOD (Standard Ease modifier)
        const btnGood = document.createElement('button');
        btnGood.innerText = "🟢 Good";
        btnGood.onclick = async () => {
            const nextInterval = Math.round(currentInterval * currentEase);
            await updateSRData(p.file.path, nextInterval, currentEase);
            btnGood.innerText = "Passed! 🚀";
            disableAll();
        };

        actionContainer.appendChild(btnForgot);
        actionContainer.appendChild(btnHard);
        actionContainer.appendChild(btnGood);

        rows.push([
            p.file.link, 
            typeIcon,
            overdueText,
            currentInterval + "d", 
            actionContainer
        ]);
    });

    dv.table(["Topic Note", "Type", "Urgency", "Interval", "Log Result"], rows);
}

// --- RENDER UPCOMING SECTION ---
dv.header(3, "🔮 Upcoming Reviews");
if (upcomingPages.length === 0) {
    dv.paragraph("No future reviews scheduled.");
} else {
    const upcomingRows = [];
    
    upcomingPages.forEach(p => {
        const currentInterval = p.sr_interval || 1;
        const typeIcon = p.type === 'practical' ? "💻 Practical" : "🧠 Theory";
        
        const nextDate = window.moment(p.sr_next, 'YYYY-MM-DD').startOf('day');
        const diff = nextDate.diff(today, 'days');
        const timelineText = diff === 1 ? "📅 Tomorrow" : `⏳ In ${diff} days`;

        upcomingRows.push([
            p.file.link,
            typeIcon,
            p.sr_next,
            timelineText,
            currentInterval + "d"
        ]);
    });

    dv.table(["Topic Note", "Type", "Next Review Date", "Timeline", "Current Interval"], upcomingRows);
}

async function updateSRData(filePath, newInterval, ease) {
    const file = app.vault.getAbstractFileByPath(filePath);
    if (file) {
        await app.fileManager.processFrontMatter(file, (fm) => {
            fm['sr_interval'] = newInterval;
            fm['sr_ease'] = ease;
            fm['sr_next'] = window.moment().add(newInterval, 'days').format('YYYY-MM-DD');
        });
    }
}
```

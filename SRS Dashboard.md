```dataviewjs
const today = window.moment().startOf('day');

// Fetch notes, assigning high priority to completely new, unreviewed notes
const pages = dv.pages('#review').where(p => {
    if (!p.sr_next) return true;
    const nextDate = window.moment(p.sr_next, 'YYYY-MM-DD').startOf('day');
    return nextDate.isSameOrBefore(today);
}).sort(p => {
    if (!p.sr_next) return 999; 
    const nextDate = window.moment(p.sr_next, 'YYYY-MM-DD').startOf('day');
    return today.diff(nextDate, 'days');
}, 'desc');

if (pages.length === 0) {
    dv.paragraph("🎉 **All caught up! No custom reviews due today.**");
} else {
    const rows = [];
    
    pages.forEach(p => {
        const currentInterval = p.sr_interval || 1;
        const currentEase = p.sr_ease || 2.5;
        
        // 1. Determine Type Icon
        const typeIcon = p.type === 'practical' ? "💻 Practical" : "🧠 Theory";
        
        // 2. Calculate Overdue Status
        let overdueText = "✨ New";
        if (p.sr_next) {
            const nextDate = window.moment(p.sr_next, 'YYYY-MM-DD').startOf('day');
            const diff = today.diff(nextDate, 'days');
            overdueText = diff === 0 ? "📅 Due Today" : `⚠️ ${diff}d Overdue`;
        }

        // 3. Generate Action Buttons Row
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

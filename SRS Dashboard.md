```dataviewjs
(async () => {
    try {
        const today = window.moment().startOf('day');

        // Inject Premium CSS styles dynamically
        const existingStyle = document.getElementById('srs-dashboard-styles');
        if (existingStyle) existingStyle.remove();

        const styleEl = document.createElement('style');
        styleEl.id = 'srs-dashboard-styles';
        styleEl.innerHTML = `
            .srs-dashboard {
                font-family: var(--font-interface);
                display: flex;
                flex-direction: column;
                gap: 16px;
            }
            .srs-header-card {
                background: linear-gradient(135deg, var(--interactive-accent) 0%, var(--interactive-accent-hover, var(--interactive-accent)) 100%);
                border-radius: 12px;
                padding: 24px;
                color: white;
                margin-bottom: 12px;
                box-shadow: 0 4px 15px rgba(0, 0, 0, 0.12);
                display: flex;
                justify-content: space-between;
                align-items: center;
                flex-wrap: wrap;
                gap: 16px;
            }
            .srs-header-title {
                margin: 0;
                font-size: 1.7em;
                font-weight: 700;
                color: #ffffff !important;
                text-shadow: 0 2px 4px rgba(0,0,0,0.15);
            }
            .srs-stats {
                display: flex;
                gap: 12px;
                flex-wrap: wrap;
            }
            .srs-stat-box {
                background: rgba(255, 255, 255, 0.12);
                backdrop-filter: blur(10px);
                border: 1px solid rgba(255, 255, 255, 0.15);
                padding: 10px 14px;
                border-radius: 8px;
                text-align: center;
                min-width: 90px;
                box-shadow: inset 0 1px 0 rgba(255,255,255,0.05);
                transition: transform 0.2s, background 0.2s;
            }
            .srs-stat-box:hover {
                transform: translateY(-2px);
                background: rgba(255, 255, 255, 0.18);
            }
            .srs-stat-val {
                font-size: 1.5em;
                font-weight: 800;
                display: block;
                line-height: 1.2;
                color: #ffffff;
            }
            .srs-stat-lbl {
                font-size: 0.72em;
                font-weight: 700;
                opacity: 0.95;
                text-transform: uppercase;
                letter-spacing: 0.5px;
                color: #ffffff;
            }
            .srs-section-title {
                font-size: 1.3em;
                font-weight: 700;
                margin-top: 24px;
                margin-bottom: 12px;
                border-bottom: 2px solid var(--background-modifier-border);
                padding-bottom: 6px;
                display: flex;
                align-items: center;
                gap: 8px;
            }
            .srs-card-grid {
                display: grid;
                grid-template-columns: 1fr;
                gap: 14px;
                margin-bottom: 20px;
            }
            @media (min-width: 600px) {
                .srs-card-grid {
                    grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
                }
            }
            .srs-card {
                background: var(--background-primary);
                border: 1px solid var(--background-modifier-border);
                border-radius: 12px;
                padding: 16px;
                box-shadow: 0 3px 8px rgba(0, 0, 0, 0.02);
                transition: all 0.25s cubic-bezier(0.4, 0, 0.2, 1);
                display: flex;
                flex-direction: column;
                justify-content: space-between;
                position: relative;
                overflow: hidden;
            }
            .srs-card::before {
                content: '';
                position: absolute;
                top: 0;
                left: 0;
                width: 4px;
                height: 100%;
                background: var(--interactive-accent);
                opacity: 0;
                transition: opacity 0.25s;
            }
            .srs-card:hover {
                transform: translateY(-3px);
                box-shadow: 0 8px 16px rgba(0, 0, 0, 0.06);
                border-color: var(--interactive-accent);
            }
            .srs-card:hover::before {
                opacity: 1;
            }
            .srs-card-title {
                font-size: 1.15em;
                font-weight: 700;
                margin-bottom: 8px;
                line-height: 1.3;
            }
            .srs-card-title a.internal-link {
                color: var(--text-normal) !important;
                text-decoration: none !important;
                border-bottom: none !important;
            }
            .srs-card-title a.internal-link:hover {
                color: var(--interactive-accent) !important;
            }
            .srs-card-meta {
                display: flex;
                flex-wrap: wrap;
                gap: 6px;
                margin-bottom: 12px;
            }
            .srs-badge {
                font-size: 0.68em;
                padding: 3px 8px;
                border-radius: 20px;
                font-weight: 700;
                text-transform: uppercase;
                letter-spacing: 0.3px;
            }
            .srs-badge-theory {
                background-color: rgba(155, 89, 182, 0.1);
                color: #9b59b6;
                border: 1px solid rgba(155, 89, 182, 0.15);
            }
            .srs-badge-practical {
                background-color: rgba(52, 152, 219, 0.1);
                color: #3498db;
                border: 1px solid rgba(52, 152, 219, 0.15);
            }
            .srs-badge-new {
                background: rgba(26, 188, 156, 0.1);
                color: #1abc9c;
                border: 1px solid rgba(26, 188, 156, 0.15);
            }
            .srs-badge-due {
                background: rgba(230, 126, 34, 0.1);
                color: #e67e22;
                border: 1px solid rgba(230, 126, 34, 0.15);
            }
            .srs-badge-overdue {
                background: rgba(231, 76, 60, 0.1);
                color: #e74c3c;
                border: 1px solid rgba(231, 76, 60, 0.15);
            }
            .srs-card-info {
                font-size: 0.8em;
                color: var(--text-muted);
                margin-bottom: 14px;
                padding-top: 6px;
                border-top: 1px dashed var(--background-modifier-border);
            }
            .srs-btn-group {
                display: flex;
                gap: 6px;
            }
            .srs-btn {
                flex: 1;
                padding: 6px 8px;
                border: none;
                border-radius: 6px;
                font-weight: 700;
                cursor: pointer;
                font-size: 0.8em;
                transition: all 0.2s;
                text-align: center;
                box-shadow: 0 1px 3px rgba(0,0,0,0.05);
            }
            .srs-btn-forgot {
                background: linear-gradient(135deg, #ff5e57 0%, #ff3b30 100%);
                color: white;
            }
            .srs-btn-forgot:hover:not(:disabled) {
                box-shadow: 0 3px 8px rgba(255, 94, 87, 0.3);
                transform: translateY(-1px);
            }
            .srs-btn-hard {
                background: linear-gradient(135deg, #ffd32a 0%, #ffc048 100%);
                color: #1e272e;
            }
            .srs-btn-hard:hover:not(:disabled) {
                box-shadow: 0 3px 8px rgba(255, 211, 42, 0.3);
                transform: translateY(-1px);
            }
            .srs-btn-good {
                background: linear-gradient(135deg, #0be881 0%, #05c46b 100%);
                color: white;
            }
            .srs-btn-good:hover:not(:disabled) {
                box-shadow: 0 3px 8px rgba(11, 232, 129, 0.3);
                transform: translateY(-1px);
            }
            .srs-btn:active:not(:disabled) {
                transform: translateY(1px);
                box-shadow: none;
            }
            .srs-btn:disabled {
                background: var(--background-modifier-border) !important;
                color: var(--text-muted) !important;
                cursor: not-allowed;
                transform: none !important;
                box-shadow: none !important;
                opacity: 0.4;
            }
            .srs-table-container {
                overflow-x: auto;
                border-radius: 8px;
                border: 1px solid var(--background-modifier-border);
                margin-top: 10px;
            }
            .srs-table {
                width: 100%;
                border-collapse: collapse;
                font-size: 0.9em;
            }
            .srs-table th {
                background-color: var(--background-secondary-alt);
                color: var(--text-muted);
                font-weight: 700;
                text-transform: uppercase;
                font-size: 0.75em;
                letter-spacing: 0.5px;
                text-align: left;
                padding: 10px 14px;
                border-bottom: 2px solid var(--background-modifier-border);
            }
            .srs-table td {
                padding: 12px 14px;
                border-bottom: 1px solid var(--background-modifier-border);
                vertical-align: middle;
            }
            .srs-table tr:last-child td {
                border-bottom: none;
            }
            .srs-table tr:hover {
                background-color: var(--background-secondary);
            }
            .srs-error-box {
                background: rgba(231, 76, 60, 0.1);
                color: #e74c3c;
                border: 1px solid rgba(231, 76, 60, 0.2);
                border-radius: 8px;
                padding: 12px;
                margin-top: 8px;
                font-family: monospace;
                white-space: pre-wrap;
                font-size: 0.85em;
            }
        `;
        this.container.appendChild(styleEl);

        // Helper function to robustly parse Dataview/Luxon dates into moment.js objects
        function parseToMoment(dateVal) {
            if (!dateVal) return null;
            if (dateVal.toJSDate && typeof dateVal.toJSDate === 'function') {
                return window.moment(dateVal.toJSDate()).startOf('day');
            }
            if (dateVal.ts) {
                return window.moment(dateVal.ts).startOf('day');
            }
            if (window.moment.isMoment(dateVal)) {
                return dateVal.startOf('day');
            }
            return window.moment(dateVal, 'YYYY-MM-DD').startOf('day');
        }

        // Fetch files
        const allPages = dv.pages('#review');

        // Filter Due and Upcoming lists
        const duePages = allPages.where(p => {
            if (!p.sr_next) return true;
            const nextDate = parseToMoment(p.sr_next);
            if (!nextDate || !nextDate.isValid()) return true;
            return nextDate.isSameOrBefore(today);
        }).sort(p => {
            if (!p.sr_next) return 999; 
            const nextDate = parseToMoment(p.sr_next);
            if (!nextDate || !nextDate.isValid()) return 998;
            return today.diff(nextDate, 'days');
        }, 'desc');

        const upcomingPages = allPages.where(p => {
            if (!p.sr_next) return false;
            const nextDate = parseToMoment(p.sr_next);
            if (!nextDate || !nextDate.isValid()) return false;
            return nextDate.isAfter(today);
        }).sort(p => {
            const nextDate = parseToMoment(p.sr_next);
            return nextDate.diff(today, 'days');
        }, 'asc');

        // Render Dashboard layout structure
        const dashboardDiv = document.createElement('div');
        dashboardDiv.className = 'srs-dashboard';
        this.container.appendChild(dashboardDiv);

        // --- 1. RENDER HEADER STATISTICS ---
        const headerCard = document.createElement('div');
        headerCard.className = 'srs-header-card';
        headerCard.innerHTML = `
            <div>
                <h2 class="srs-header-title">🧠 Spaced Repetition</h2>
                <div style="font-size: 0.85em; opacity: 0.9; margin-top: 4px; font-weight: 500;">Optimize your retention and master concepts</div>
            </div>
            <div class="srs-stats">
                <div class="srs-stat-box">
                    <span class="srs-stat-val">${duePages.length}</span>
                    <span class="srs-stat-lbl">Due Now</span>
                </div>
                <div class="srs-stat-box">
                    <span class="srs-stat-val">${upcomingPages.length}</span>
                    <span class="srs-stat-lbl">Upcoming</span>
                </div>
                <div class="srs-stat-box">
                    <span class="srs-stat-val">${allPages.length}</span>
                    <span class="srs-stat-lbl">Total</span>
                </div>
            </div>
        `;
        dashboardDiv.appendChild(headerCard);

        // --- 2. RENDER DUE SECTION ---
        const dueTitle = document.createElement('div');
        dueTitle.className = 'srs-section-title';
        dueTitle.innerHTML = `<span>📅</span> Due & Overdue Reviews`;
        dashboardDiv.appendChild(dueTitle);

        if (duePages.length === 0) {
            const emptyState = document.createElement('div');
            emptyState.style.cssText = "padding: 30px; text-align: center; border-radius: 12px; border: 2px dashed var(--background-modifier-border); color: var(--text-muted); font-weight: 600;";
            emptyState.innerHTML = "🎉 All caught up! No reviews due today.";
            dashboardDiv.appendChild(emptyState);
        } else {
            const grid = document.createElement('div');
            grid.className = 'srs-card-grid';
            dashboardDiv.appendChild(grid);
            
            for (const p of duePages) {
                try {
                    const card = document.createElement('div');
                    card.className = 'srs-card';
                    
                    const currentInterval = p.sr_interval || 1;
                    const currentEase = p.sr_ease || 2.5;
                    
                    // Tags/Badge for Type
                    const isPractical = p.type === 'practical';
                    const typeClass = isPractical ? 'srs-badge-practical' : 'srs-badge-theory';
                    const typeLabel = isPractical ? '💻 Practical' : '🧠 Theory';
                    
                    // Badge for Urgency
                    let urgencyClass = 'srs-badge-new';
                    let urgencyText = '✨ New';
                    if (p.sr_next) {
                        const nextDate = parseToMoment(p.sr_next);
                        if (nextDate && nextDate.isValid()) {
                            const diff = today.diff(nextDate, 'days');
                            if (diff === 0) {
                                urgencyClass = 'srs-badge-due';
                                urgencyText = '📅 Due Today';
                            } else if (diff > 0) {
                                urgencyClass = 'srs-badge-overdue';
                                urgencyText = `⚠️ ${diff}d Overdue`;
                            }
                        }
                    }
                    
                    // Title Links (Synchronous native wiki-link)
                    const titleContainer = document.createElement('div');
                    titleContainer.className = 'srs-card-title';
                    
                    const linkAnchor = document.createElement('a');
                    linkAnchor.className = 'internal-link';
                    linkAnchor.href = p.file.path;
                    linkAnchor.setAttribute('data-href', p.file.path);
                    linkAnchor.innerText = p.file.name;
                    titleContainer.appendChild(linkAnchor);
                    card.appendChild(titleContainer);
                    
                    // Badges metadata container
                    const badgesContainer = document.createElement('div');
                    badgesContainer.className = 'srs-card-meta';
                    badgesContainer.innerHTML = `
                        <span class="srs-badge ${typeClass}">${typeLabel}</span>
                        <span class="srs-badge ${urgencyClass}">${urgencyText}</span>
                    `;
                    card.appendChild(badgesContainer);
                    
                    // Parameters stats info
                    const info = document.createElement('div');
                    info.className = 'srs-card-info';
                    info.innerHTML = `
                        <div>Interval: <b>${currentInterval}d</b> &nbsp;&bull;&nbsp; Ease: <b>${currentEase}x</b></div>
                    `;
                    card.appendChild(info);
                    
                    // Buttons block
                    const btnGroup = document.createElement('div');
                    btnGroup.className = 'srs-btn-group';
                    
                    const disableAll = () => {
                        btnForgot.disabled = true;
                        btnHard.disabled = true;
                        btnGood.disabled = true;
                    };
                    
                    // 🔴 Forgot Button
                    const btnForgot = document.createElement('button');
                    btnForgot.className = 'srs-btn srs-btn-forgot';
                    btnForgot.innerText = "🔴 Forgot";
                    btnForgot.addEventListener('click', async (e) => {
                        e.preventDefault();
                        new Notice(`Updating: ${p.file.name} (Forgot)`);
                        try {
                            await updateSRData(p.file.path, 1, currentEase);
                            btnForgot.innerText = "Reset 🔄";
                            disableAll();
                        } catch (err) {
                            new Notice(`Error: ${err.message}`);
                        }
                    });
                    
                    // 🟡 Hard Button
                    const btnHard = document.createElement('button');
                    btnHard.className = 'srs-btn srs-btn-hard';
                    btnHard.innerText = "🟡 Hard";
                    btnHard.addEventListener('click', async (e) => {
                        e.preventDefault();
                        const nextInterval = Math.max(1, Math.round(currentInterval * 1.2));
                        new Notice(`Updating: ${p.file.name} (Hard: ${nextInterval}d)`);
                        try {
                            await updateSRData(p.file.path, nextInterval, currentEase);
                            btnHard.innerText = "Saved 🩹";
                            disableAll();
                        } catch (err) {
                            new Notice(`Error: ${err.message}`);
                        }
                    });
                    
                    // 🟢 Good Button
                    const btnGood = document.createElement('button');
                    btnGood.className = 'srs-btn srs-btn-good';
                    btnGood.innerText = "🟢 Good";
                    btnGood.addEventListener('click', async (e) => {
                        e.preventDefault();
                        const nextInterval = Math.round(currentInterval * currentEase);
                        new Notice(`Updating: ${p.file.name} (Good: ${nextInterval}d)`);
                        try {
                            await updateSRData(p.file.path, nextInterval, currentEase);
                            btnGood.innerText = "Passed! 🚀";
                            disableAll();
                        } catch (err) {
                            new Notice(`Error: ${err.message}`);
                        }
                    });
                    
                    btnGroup.appendChild(btnForgot);
                    btnGroup.appendChild(btnHard);
                    btnGroup.appendChild(btnGood);
                    card.appendChild(btnGroup);
                    
                    grid.appendChild(card);
                } catch (cardErr) {
                    const errBox = document.createElement('div');
                    errBox.className = 'srs-error-box';
                    errBox.innerText = `Error rendering card for ${p.file.path}:\n${cardErr.stack || cardErr}`;
                    dashboardDiv.appendChild(errBox);
                }
            }
        }

        // --- 3. RENDER UPCOMING SECTION ---
        const upcomingTitle = document.createElement('div');
        upcomingTitle.className = 'srs-section-title';
        upcomingTitle.innerHTML = `<span>🔮</span> Upcoming Reviews`;
        dashboardDiv.appendChild(upcomingTitle);

        if (upcomingPages.length === 0) {
            const emptyState = document.createElement('div');
            emptyState.style.cssText = "padding: 16px; text-align: center; color: var(--text-muted); font-size: 0.95em;";
            emptyState.innerText = "No upcoming reviews scheduled.";
            dashboardDiv.appendChild(emptyState);
        } else {
            const tableContainer = document.createElement('div');
            tableContainer.className = 'srs-table-container';
            dashboardDiv.appendChild(tableContainer);
            
            const table = document.createElement('table');
            table.className = 'srs-table';
            table.innerHTML = `
                <thead>
                    <tr>
                        <th>Topic Note</th>
                        <th>Type</th>
                        <th>Next Review</th>
                        <th>Timeline</th>
                        <th>Interval</th>
                    </tr>
                </thead>
                <tbody></tbody>
            `;
            tableContainer.appendChild(table);
            
            const tbody = table.querySelector('tbody');
            
            for (const p of upcomingPages) {
                try {
                    const tr = document.createElement('tr');
                    
                    const tdNote = document.createElement('td');
                    tdNote.style.fontWeight = "600";
                    
                    const linkAnchor = document.createElement('a');
                    linkAnchor.className = 'internal-link';
                    linkAnchor.href = p.file.path;
                    linkAnchor.setAttribute('data-href', p.file.path);
                    linkAnchor.innerText = p.file.name;
                    tdNote.appendChild(linkAnchor);
                    
                    const isPractical = p.type === 'practical';
                    const typeLabel = isPractical ? '💻 Practical' : '🧠 Theory';
                    const tdType = document.createElement('td');
                    tdType.innerText = typeLabel;
                    
                    const nextDate = parseToMoment(p.sr_next);
                    const tdDate = document.createElement('td');
                    tdDate.innerText = nextDate.format('YYYY-MM-DD');
                    
                    const diff = nextDate.diff(today, 'days');
                    const timelineText = diff === 1 ? "📅 Tomorrow" : `⏳ In ${diff} days`;
                    const tdTimeline = document.createElement('td');
                    tdTimeline.innerText = timelineText;
                    
                    const currentInterval = p.sr_interval || 1;
                    const tdInterval = document.createElement('td');
                    tdInterval.innerText = currentInterval + "d";
                    
                    tr.appendChild(tdNote);
                    tr.appendChild(tdType);
                    tr.appendChild(tdDate);
                    tr.appendChild(tdTimeline);
                    tr.appendChild(tdInterval);
                    
                    tbody.appendChild(tr);
                } catch (trErr) {
                    const errBox = document.createElement('div');
                    errBox.className = 'srs-error-box';
                    errBox.innerText = `Error rendering row for ${p.file.path}:\n${trErr.stack || trErr}`;
                    dashboardDiv.appendChild(errBox);
                }
            }
        }

        // Collapsible Debug Info Section at the very bottom
        const debugDetails = document.createElement('details');
        debugDetails.style.cssText = "margin-top: 40px; padding: 12px; font-size: 0.8em; color: var(--text-muted); border-top: 1px solid var(--background-modifier-border); cursor: pointer;";
        debugDetails.innerHTML = `<summary>🔍 Debug Info (Click to Expand)</summary>`;

        const debugContent = document.createElement('div');
        debugContent.style.paddingTop = "10px";

        const exTarget = allPages.where(p => p.file.name === "example");
        let debugText = `Total Pages with #review: <b>${allPages.length}</b><br/>`;
        if (exTarget.length > 0) {
            const ex = exTarget[0];
            const mDate = parseToMoment(ex.sr_next);
            debugText += `✅ <b>example.md</b> in Dataview:<br/>`;
            debugText += `- Path: \`${ex.file.path}\`<br/>`;
            debugText += `- Tags: \`${JSON.stringify(ex.file.tags || [])}\`<br/>`;
            debugText += `- sr_next raw: \`${ex.sr_next}\`<br/>`;
            debugText += `- sr_next parsed: \`${mDate ? mDate.format('YYYY-MM-DD') : 'Invalid'}\`<br/>`;
        } else {
            debugText += `❌ <b>example.md</b> was not found in #review query.`;
        }
        debugContent.innerHTML = debugText;
        debugDetails.appendChild(debugContent);
        this.container.appendChild(debugDetails);

    } catch (topErr) {
        const errDiv = document.createElement('div');
        errDiv.style.cssText = "padding: 16px; background: rgba(231, 76, 60, 0.1); color: #e74c3c; border: 1px solid #e74c3c; border-radius: 8px; font-family: monospace; white-space: pre-wrap;";
        errDiv.innerText = `Top-level Error:\n${topErr.stack || topErr}`;
        this.container.appendChild(errDiv);
    }

    async function updateSRData(filePath, newInterval, ease) {
        const file = app.vault.getAbstractFileByPath(filePath);
        if (!file) {
            throw new Error(`File not found at path: ${filePath}`);
        }
        await app.fileManager.processFrontMatter(file, (fm) => {
            fm['sr_interval'] = newInterval;
            fm['sr_ease'] = ease;
            fm['sr_next'] = window.moment().add(newInterval, 'days').format('YYYY-MM-DD');
        });
        new Notice(`Successfully updated ${file.name}!`);
    }
})();
```

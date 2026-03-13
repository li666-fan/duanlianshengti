<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>21天手机依赖摆脱计划 - 每日打卡表</title>
    <style>
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', 'Microsoft YaHei', sans-serif;
        }

        body {
            background-color: #0a0a0a;
            color: #e6e6e6;
            line-height: 1.6;
            padding: 20px;
            max-width: 1200px;
            margin: 0 auto;
        }

        .container {
            background-color: #121212;
            border-radius: 12px;
            padding: 30px;
            box-shadow: 0 8px 30px rgba(218, 165, 32, 0.08);
            border: 1px solid #333;
        }

        header {
            text-align: center;
            margin-bottom: 30px;
            padding-bottom: 20px;
            border-bottom: 2px solid #DAA520;
        }

        h1 {
            color: #DAA520;
            font-size: 2.5rem;
            margin-bottom: 10px;
        }

        .subtitle {
            color: #b0b0b0;
            font-size: 1.1rem;
            max-width: 800px;
            margin: 0 auto 20px;
        }

        .phase-container {
            display: flex;
            justify-content: space-between;
            flex-wrap: wrap;
            gap: 20px;
            margin-bottom: 30px;
        }

        .phase {
            flex: 1;
            min-width: 300px;
            background: linear-gradient(to bottom right, #1a1a1a, #222);
            border-radius: 10px;
            padding: 20px;
            border-left: 4px solid #DAA520;
        }

        .phase h2 {
            color: #DAA520;
            margin-bottom: 15px;
            font-size: 1.5rem;
        }

        .phase p {
            color: #ccc;
            margin-bottom: 10px;
        }

        .controls {
            display: flex;
            gap: 15px;
            margin-bottom: 30px;
            flex-wrap: wrap;
            align-items: center;
            background-color: #1a1a1a;
            padding: 20px;
            border-radius: 10px;
        }

        .input-group {
            display: flex;
            flex-direction: column;
            flex: 1;
            min-width: 200px;
        }

        .input-group label {
            margin-bottom: 8px;
            color: #DAA520;
            font-weight: 500;
        }

        .input-group input, .input-group textarea, .input-group select {
            padding: 12px 15px;
            border: 1px solid #444;
            border-radius: 6px;
            background-color: #222;
            color: #e6e6e6;
            font-size: 1rem;
        }

        .input-group textarea {
            resize: vertical;
            min-height: 60px;
        }

        .btn {
            padding: 12px 25px;
            border: none;
            border-radius: 6px;
            cursor: pointer;
            font-weight: 600;
            font-size: 1rem;
            transition: all 0.3s ease;
        }

        .btn-primary {
            background-color: #DAA520;
            color: #121212;
        }

        .btn-primary:hover {
            background-color: #f0c040;
            transform: translateY(-2px);
        }

        .btn-secondary {
            background-color: #333;
            color: #e6e6e6;
        }

        .btn-secondary:hover {
            background-color: #444;
        }

        .btn-danger {
            background-color: #8B0000;
            color: #e6e6e6;
        }

        .btn-danger:hover {
            background-color: #a00;
        }

        .table-container {
            overflow-x: auto;
            border-radius: 8px;
            border: 1px solid #333;
        }

        table {
            width: 100%;
            border-collapse: collapse;
            min-width: 900px;
        }

        thead {
            background-color: #1a1a1a;
        }

        th {
            padding: 18px 15px;
            text-align: left;
            color: #DAA520;
            font-weight: 600;
            border-bottom: 2px solid #DAA520;
        }

        td {
            padding: 15px;
            border-bottom: 1px solid #333;
        }

        tbody tr {
            background-color: #181818;
        }

        tbody tr:nth-child(even) {
            background-color: #1c1c1c;
        }

        tbody tr:hover {
            background-color: #222;
        }

        .day-cell {
            text-align: center;
            font-weight: 600;
            color: #DAA520;
            width: 60px;
        }

        .checkbox-cell {
            text-align: center;
            width: 100px;
        }

        .checkbox-container {
            display: inline-block;
            width: 24px;
            height: 24px;
            position: relative;
        }

        .checkbox-container input {
            opacity: 0;
            width: 0;
            height: 0;
            position: absolute;
        }

        .checkmark {
            position: absolute;
            top: 0;
            left: 0;
            height: 24px;
            width: 24px;
            background-color: #222;
            border: 2px solid #444;
            border-radius: 4px;
            cursor: pointer;
            transition: all 0.2s ease;
        }

        .checkbox-container input:checked ~ .checkmark {
            background-color: #DAA520;
            border-color: #DAA520;
        }

        .checkmark:after {
            content: "";
            position: absolute;
            display: none;
            left: 8px;
            top: 4px;
            width: 5px;
            height: 10px;
            border: solid #121212;
            border-width: 0 2px 2px 0;
            transform: rotate(45deg);
        }

        .checkbox-container input:checked ~ .checkmark:after {
            display: block;
        }

        .insight-cell {
            max-width: 300px;
        }

        .insight-text {
            color: #b0b0b0;
            font-size: 0.9rem;
            line-height: 1.4;
        }

        .empty-row td {
            text-align: center;
            padding: 40px;
            color: #888;
            font-style: italic;
        }

        .actions-cell {
            display: flex;
            gap: 8px;
        }

        .action-btn {
            background: none;
            border: none;
            color: #DAA520;
            cursor: pointer;
            padding: 5px;
            font-size: 1.1rem;
        }

        .action-btn:hover {
            color: #f0c040;
        }

        footer {
            margin-top: 30px;
            text-align: center;
            color: #888;
            font-size: 0.9rem;
            padding-top: 20px;
            border-top: 1px solid #333;
        }

        .stats {
            display: flex;
            justify-content: space-around;
            background-color: #1a1a1a;
            padding: 20px;
            border-radius: 10px;
            margin-bottom: 20px;
        }

        .stat-box {
            text-align: center;
        }

        .stat-value {
            font-size: 2.2rem;
            color: #DAA520;
            font-weight: 700;
        }

        .stat-label {
            color: #b0b0b0;
            font-size: 0.9rem;
        }

        @media (max-width: 768px) {
            .phase-container {
                flex-direction: column;
            }
            
            .phase {
                min-width: 100%;
            }
            
            h1 {
                font-size: 2rem;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <h1>21天摆脱手机依赖计划</h1>
            <p class="subtitle">基于"物理隔离"、"时间分区"、"替代活动"三大核心框架，通过21天系统训练，重建您与科技的健康关系，重获对注意力的掌控权。</p>
        </header>

        <div class="phase-container">
            <div class="phase">
                <h2>第1周 | 适应期</h2>
                <p><strong>目标：</strong>建立手机使用规则</p>
                <p><strong>核心任务：</strong></p>
                <p>• 删除娱乐APP，关闭非必要通知</p>
                <p>• 设立"无手机时段"</p>
                <p>• 寻找替代活动（阅读、运动等）</p>
            </div>
            
            <div class="phase">
                <h2>第2周 | 巩固期</h2>
                <p><strong>目标：</strong>延长无手机时间，培养新习惯</p>
                <p><strong>核心任务：</strong></p>
                <p>• 使用手机定时锁盒</p>
                <p>• 设立"数字排毒"时段</p>
                <p>• 扩展替代活动（兴趣小组、手工艺等）</p>
            </div>
            
            <div class="phase">
                <h2>第3周 | 习惯期</h2>
                <p><strong>目标：</strong>内化自律，建立新生活方式</p>
                <p><strong>核心任务：</strong></p>
                <p>• 尝试"无手机日"挑战</p>
                <p>• 制定长期数字健康计划</p>
                <p>• 用真实世界活动替代虚拟快感</p>
            </div>
        </div>

        <div class="stats">
            <div class="stat-box">
                <div class="stat-value" id="completed-days">0</div>
                <div class="stat-label">已坚持天数</div>
            </div>
            <div class="stat-box">
                <div class="stat-value" id="completion-rate">0%</div>
                <div class="stat-label">总完成率</div>
            </div>
            <div class="stat-box">
                <div class="stat-value" id="current-streak">0</div>
                <div class="stat-label">当前连续打卡</div>
            </div>
        </div>

        <div class="controls">
            <div class="input-group">
                <label for="day-input">计划天数 (1-21)</label>
                <input type="number" id="day-input" min="1" max="21" value="1">
            </div>
            
            <div class="input-group">
                <label for="physical-isolation">物理隔离完成情况</label>
                <select id="physical-isolation">
                    <option value="未开始">未开始</option>
                    <option value="进行中">进行中</option>
                    <option value="已完成">已完成</option>
                </select>
            </div>
            
            <div class="input-group">
                <label for="time-partition">时间分区遵守情况</label>
                <select id="time-partition">
                    <option value="未开始">未开始</option>
                    <option value="部分遵守">部分遵守</option>
                    <option value="完全遵守">完全遵守</option>
                </select>
            </div>
            
            <div class="input-group">
                <label for="alternative-activity">替代活动执行情况</label>
                <select id="alternative-activity">
                    <option value="未执行">未执行</option>
                    <option value="部分执行">部分执行</option>
                    <option value="完全执行">完全执行</option>
                </select>
            </div>
        </div>

        <div class="controls">
            <div class="input-group" style="flex: 2;">
                <label for="insight-input">今日感悟/困难</label>
                <textarea id="insight-input" placeholder="记录今天的感受、遇到的困难或突破..."></textarea>
            </div>
            
            <div style="display: flex; flex-direction: column; justify-content: center; gap: 10px;">
                <button class="btn btn-primary" id="add-btn">添加/更新记录</button>
                <button class="btn btn-secondary" id="clear-btn">清空所有记录</button>
            </div>
        </div>

        <div class="table-container">
            <table id="tracker-table">
                <thead>
                    <tr>
                        <th>天数</th>
                        <th>物理隔离完成</th>
                        <th>时间分区遵守</th>
                        <th>替代活动执行</th>
                        <th>今日感悟/困难</th>
                        <th>操作</th>
                    </tr>
                </thead>
                <tbody id="table-body">
                    <!-- 表格内容将通过JavaScript动态生成 -->
                </tbody>
            </table>
        </div>

        <footer>
            <p>真正的自由不是随时在线，而是随时可以选择离线。</p>
            <p>数据保存在您的浏览器本地，清除浏览器数据会重置记录 | 设计：元宝</p>
        </footer>
    </div>

    <script>
        document.addEventListener('DOMContentLoaded', function() {
            const trackerTable = document.getElementById('tracker-table');
            const tableBody = document.getElementById('table-body');
            const dayInput = document.getElementById('day-input');
            const physicalIsolationSelect = document.getElementById('physical-isolation');
            const timePartitionSelect = document.getElementById('time-partition');
            const alternativeActivitySelect = document.getElementById('alternative-activity');
            const insightInput = document.getElementById('insight-input');
            const addButton = document.getElementById('add-btn');
            const clearButton = document.getElementById('clear-btn');
            
            const completedDaysElement = document.getElementById('completed-days');
            const completionRateElement = document.getElementById('completion-rate');
            const currentStreakElement = document.getElementById('current-streak');

            // 从localStorage加载数据
            let records = JSON.parse(localStorage.getItem('phoneDetoxRecords')) || [];
            
            // 初始化表格
            function initTable() {
                // 先清空表格
                tableBody.innerHTML = '';
                
                if (records.length === 0) {
                    // 如果没有记录，显示空行
                    const emptyRow = document.createElement('tr');
                    emptyRow.className = 'empty-row';
                    emptyRow.innerHTML = `<td colspan="6">暂无打卡记录，请添加您的第一天打卡！</td>`;
                    tableBody.appendChild(emptyRow);
                } else {
                    // 按天数排序
                    records.sort((a, b) => a.day - b.day);
                    
                    // 添加每一行记录
                    records.forEach(record => {
                        addRowToTable(record);
                    });
                }
                
                updateStats();
            }
            
            // 添加行到表格
            function addRowToTable(record) {
                const row = document.createElement('tr');
                
                // 创建状态选项
                const statusOptions = ['未开始', '进行中', '已完成', '部分遵守', '完全遵守', '未执行', '部分执行', '完全执行'];
                
                // 计算完成状态
                const isCompleted = 
                    (record.physicalIsolation === '已完成' || record.physicalIsolation === '完全遵守' || record.physicalIsolation === '完全执行') &&
                    (record.timePartition === '已完成' || record.timePartition === '完全遵守' || record.timePartition === '完全执行') &&
                    (record.alternativeActivity === '已完成' || record.alternativeActivity === '完全遵守' || record.alternativeActivity === '完全执行');
                
                row.innerHTML = `
                    <td class="day-cell">第 ${record.day} 天</td>
                    <td>
                        <select class="status-select" data-field="physicalIsolation" data-day="${record.day}">
                            ${statusOptions.map(opt => 
                                `<option value="${opt}" ${record.physicalIsolation === opt ? 'selected' : ''}>${opt}</option>`
                            ).join('')}
                        </select>
                    </td>
                    <td>
                        <select class="status-select" data-field="timePartition" data-day="${record.day}">
                            ${statusOptions.map(opt => 
                                `<option value="${opt}" ${record.timePartition === opt ? 'selected' : ''}>${opt}</option>`
                            ).join('')}
                        </select>
                    </td>
                    <td>
                        <select class="status-select" data-field="alternativeActivity" data-day="${record.day}">
                            ${statusOptions.map(opt => 
                                `<option value="${opt}" ${record.alternativeActivity === opt ? 'selected' : ''}>${opt}</option>`
                            ).join('')}
                        </select>
                    </td>
                    <td class="insight-cell">
                        <div class="insight-text">${record.insight || '暂无记录'}</div>
                        <textarea class="insight-edit" data-day="${record.day}" style="display: none; width: 100%; margin-top: 5px; background-color: #222; color: #e6e6e6; border: 1px solid #444; padding: 8px; border-radius: 4px;">${record.insight || ''}</textarea>
                        <button class="action-btn edit-insight-btn" data-day="${record.day}" style="font-size: 0.8rem; margin-top: 5px;">${record.insight ? '编辑' : '添加'}</button>
                    </td>
                    <td>
                        <div class="actions-cell">
                            <button class="action-btn delete-btn" data-day="${record.day}" title="删除">🗑️</button>
                        </div>
                    </td>
                `;
                
                tableBody.appendChild(row);
                
                // 移除空行提示（如果存在）
                const emptyRow = document.querySelector('.empty-row');
                if (emptyRow) {
                    emptyRow.remove();
                }
            }
            
            // 更新统计信息
            function updateStats() {
                if (records.length === 0) {
                    completedDaysElement.textContent = '0';
                    completionRateElement.textContent = '0%';
                    currentStreakElement.textContent = '0';
                    return;
                }
                
                // 已坚持天数（有记录的天数）
                completedDaysElement.textContent = records.length;
                
                // 计算完成率（三项都完成的记录比例）
                const completedRecords = records.filter(record => 
                    (record.physicalIsolation === '已完成' || record.physicalIsolation === '完全遵守' || record.physicalIsolation === '完全执行') &&
                    (record.timePartition === '已完成' || record.timePartition === '完全遵守' || record.timePartition === '完全执行') &&
                    (record.alternativeActivity === '已完成' || record.alternativeActivity === '完全遵守' || record.alternativeActivity === '完全执行')
                ).length;
                
                const completionRate = Math.round((completedRecords / records.length) * 100);
                completionRateElement.textContent = `${completionRate}%`;
                
                // 计算当前连续打卡天数
                const sortedDays = records.map(r => r.day).sort((a, b) => a - b);
                let currentStreak = 0;
                let expectedDay = 1;
                
                for (let day of sortedDays) {
                    if (day === expectedDay) {
                        currentStreak++;
                        expectedDay++;
                    } else {
                        break;
                    }
                }
                
                currentStreakElement.textContent = currentStreak;
            }
            
            // 添加/更新记录
            function addOrUpdateRecord() {
                const day = parseInt(dayInput.value);
                const physicalIsolation = physicalIsolationSelect.value;
                const timePartition = timePartitionSelect.value;
                const alternativeActivity = alternativeActivitySelect.value;
                const insight = insightInput.value.trim();
                
                if (day < 1 || day > 21) {
                    alert('天数必须在1-21之间');
                    return;
                }
                
                // 检查是否已存在该天的记录
                const existingIndex = records.findIndex(record => record.day === day);
                
                const record = {
                    day,
                    physicalIsolation,
                    timePartition,
                    alternativeActivity,
                    insight,
                    updatedAt: new Date().toISOString()
                };
                
                if (existingIndex >= 0) {
                    // 更新现有记录
                    records[existingIndex] = record;
                } else {
                    // 添加新记录
                    records.push(record);
                }
                
                // 保存到localStorage
                localStorage.setItem('phoneDetoxRecords', JSON.stringify(records));
                
                // 重新初始化表格
                initTable();
                
                // 清空表单（第1天除外，方便连续记录）
                if (day === 21) {
                    dayInput.value = 1;
                } else {
                    dayInput.value = day + 1;
                }
                
                insightInput.value = '';
                
                // 可选：显示成功消息
                alert(`第${day}天记录已${existingIndex >= 0 ? '更新' : '添加'}！`);
            }
            
            // 清空所有记录
            function clearAllRecords() {
                if (confirm('确定要清空所有打卡记录吗？此操作不可撤销。')) {
                    records = [];
                    localStorage.removeItem('phoneDetoxRecords');
                    initTable();
                    alert('所有记录已清空！');
                }
            }
            
            // 删除特定天数的记录
            function deleteRecord(day) {
                if (confirm(`确定要删除第${day}天的记录吗？`)) {
                    records = records.filter(record => record.day !== day);
                    localStorage.setItem('phoneDetoxRecords', JSON.stringify(records));
                    initTable();
                }
            }
            
            // 更新记录状态
            function updateRecordStatus(day, field, value) {
                const recordIndex = records.findIndex(record => record.day === day);
                
                if (recordIndex >= 0) {
                    records[recordIndex][field] = value;
                    records[recordIndex].updatedAt = new Date().toISOString();
                    localStorage.setItem('phoneDetoxRecords', JSON.stringify(records));
                    updateStats();
                }
            }
            
            // 更新记录感悟
            function updateRecordInsight(day, insight) {
                const recordIndex = records.findIndex(record => record.day === day);
                
                if (recordIndex >= 0) {
                    records[recordIndex].insight = insight;
                    records[recordIndex].updatedAt = new Date().toISOString();
                    localStorage.setItem('phoneDetoxRecords', JSON.stringify(records));
                    initTable(); // 重新渲染以更新显示
                }
            }
            
            // 事件委托处理表格内的交互
            tableBody.addEventListener('change', function(e) {
                if (e.target.classList.contains('status-select')) {
                    const day = parseInt(e.target.getAttribute('data-day'));
                    const field = e.target.getAttribute('data-field');
                    const value = e.target.value;
                    
                    updateRecordStatus(day, field, value);
                }
            });
            
            tableBody.addEventListener('click', function(e) {
                // 处理删除按钮
                if (e.target.classList.contains('delete-btn')) {
                    const day = parseInt(e.target.getAttribute('data-day'));
                    deleteRecord(day);
                }
                
                // 处理编辑感悟按钮
                if (e.target.classList.contains('edit-insight-btn')) {
                    const day = parseInt(e.target.getAttribute('data-day'));
                    const cell = e.target.closest('td');
                    const insightText = cell.querySelector('.insight-text');
                    const insightEdit = cell.querySelector('.insight-edit');
                    const editBtn = e.target;
                    
                    if (insightEdit.style.display === 'none') {
                        // 切换到编辑模式
                        insightText.style.display = 'none';
                        insightEdit.style.display = 'block';
                        editBtn.textContent = '保存';
                    } else {
                        // 保存感悟
                        const newInsight = insightEdit.value.trim();
                        updateRecordInsight(day, newInsight);
                    }
                }
            });
            
            // 添加按钮事件
            addButton.addEventListener('click', addOrUpdateRecord);
            
            // 清空按钮事件
            clearButton.addEventListener('click', clearAllRecords);
            
            // 回车键快速提交
            insightInput.addEventListener('keypress', function(e) {
                if (e.key === 'Enter' && !e.shiftKey) {
                    e.preventDefault();
                    addOrUpdateRecord();
                }
            });
            
            // 初始化表格
            initTable();
        });
    </script>
</body>
</html>

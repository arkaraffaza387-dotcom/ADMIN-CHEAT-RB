<html lang="id">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>🔐 Admin Panel • AzferModz</title>
<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;600;700;800;900&family=Orbitron:wght@700;900&display=swap" rel="stylesheet">
<link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css" rel="stylesheet">
<style>
* { margin:0; padding:0; box-sizing:border-box; font-family:'Poppins',sans-serif; }

body {
    background: radial-gradient(ellipse at center, #1a0000 0%, #0a0000 50%, #000000 100%);
    min-height: 100vh;
    padding: 20px;
    color: #fff;
    display: flex;
    justify-content: center;
    align-items: flex-start;
}
body::before {
    content: "";
    position: fixed;
    inset: 0;
    background:
        radial-gradient(circle at 20% 20%, rgba(139, 0, 0, 0.3) 0%, transparent 50%),
        radial-gradient(circle at 80% 80%, rgba(184, 134, 11, 0.2) 0%, transparent 50%);
    pointer-events: none;
    z-index: 0;
}

.container {
    width: 100%;
    max-width: 920px;
    background: linear-gradient(165deg, #1a0a0a 0%, #0d0505 30%, #1a0a0a 70%, #0a0000 100%);
    border: 2px solid #b8860b;
    border-radius: 30px;
    box-shadow: 0 30px 60px -12px rgba(139, 0, 0, 0.8),
                0 0 0 1px rgba(255, 215, 0, 0.3) inset,
                0 0 30px rgba(184, 134, 11, 0.3);
    overflow: hidden;
    position: relative;
    z-index: 1;
}
.container::before {
    content: "";
    position: absolute;
    top: -2px;
    left: 20%;
    right: 20%;
    height: 3px;
    background: linear-gradient(90deg, transparent, #ffed4a, #ffd700, #ffed4a, transparent);
    filter: blur(1px);
    animation: shine 3s ease-in-out infinite;
}
@keyframes shine {
    0%,100% { opacity:0.5; transform:scaleX(0.8); }
    50% { opacity:1; transform:scaleX(1); }
}

.header {
    background: linear-gradient(135deg, rgba(139,0,0,0.4), rgba(40,20,20,0.6));
    padding: 22px 24px;
    text-align: center;
    border-bottom: 1px solid rgba(184, 134, 11, 0.3);
}
.header h1 {
    font-family: 'Orbitron', sans-serif;
    font-size: 20px;
    color: #ffd700;
    letter-spacing: 3px;
    text-shadow: 0 0 20px rgba(255, 215, 0, 0.5);
}
.header p {
    font-size: 11px;
    color: #cc9999;
    letter-spacing: 2px;
    text-transform: uppercase;
    margin-top: 5px;
}

.info-bar {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 14px 24px;
    background: rgba(0,0,0,0.3);
    border-bottom: 1px solid rgba(184, 134, 11, 0.2);
    font-size: 12px;
    color: #cc9999;
    flex-wrap: wrap;
    gap: 8px;
}
.info-bar strong { color: #ffd700; }

.content { padding: 26px; }

.form-group { margin-bottom: 14px; text-align: left; }
.form-label {
    display: block;
    color: #ffd700;
    font-size: 11px;
    font-weight: 700;
    letter-spacing: 1.5px;
    margin-bottom: 6px;
    text-transform: uppercase;
}
.form-input, .form-select, .form-textarea {
    width: 100%;
    padding: 13px 16px;
    background: #0d0202;
    border: 1px solid rgba(184, 134, 11, 0.5);
    border-radius: 12px;
    color: #ffed4a;
    font-size: 13px;
    font-family: 'Poppins', sans-serif;
    transition: all 0.3s ease;
    outline: none;
}
.form-input:focus, .form-select:focus, .form-textarea:focus {
    border-color: #ffd700;
    box-shadow: 0 0 15px rgba(255, 215, 0, 0.3);
}
.form-textarea { font-family: 'Courier New', monospace; resize: vertical; min-height: 60px; }

.btn {
    padding: 13px 22px;
    border: none;
    border-radius: 50px;
    font-family: 'Poppins', sans-serif;
    font-size: 12px;
    font-weight: 800;
    cursor: pointer;
    letter-spacing: 1.2px;
    text-transform: uppercase;
    display: inline-flex;
    align-items: center;
    justify-content: center;
    gap: 8px;
    transition: all 0.3s ease;
}
.btn-primary {
    background: linear-gradient(135deg, #8b0000, #cc0000);
    border: 1.5px solid #ffd700;
    color: #ffed4a;
    box-shadow: 0 8px 25px -5px rgba(139, 0, 0, 0.8);
    width: 100%;
}
.btn-primary:hover:not(:disabled) { transform: scale(1.02); box-shadow: 0 12px 35px -6px rgba(204, 0, 0, 0.9); }
.btn-primary:disabled { opacity: 0.5; cursor: not-allowed; }

.btn-danger {
    background: linear-gradient(135deg, #7a2020, #3a1010);
    border: 1px solid rgba(255,100,100,0.4);
    color: #ff8888;
    padding: 8px 14px;
    font-size: 10px;
    border-radius: 8px;
}
.btn-danger:hover { background: rgba(255,100,100,0.2); }

.btn-sm { padding: 8px 14px; font-size: 10px; }

.alert {
    padding: 13px 16px;
    border-radius: 12px;
    font-size: 12px;
    margin-bottom: 16px;
    display: none;
    line-height: 1.5;
}
.alert.show { display: block; animation: fadeIn 0.3s ease; }
@keyframes fadeIn { from { opacity:0; transform:translateY(-5px); } to { opacity:1; transform:translateY(0); } }
.alert-info { background: rgba(100,150,255,0.12); border: 1px solid rgba(100,150,255,0.4); color: #a0c0ff; }
.alert-error { background: rgba(255,50,50,0.12); border: 1px solid rgba(255,50,50,0.4); color: #ff9999; }
.alert-success { background: rgba(50,255,100,0.12); border: 1px solid rgba(50,255,100,0.4); color: #99ff99; }

.form-section {
    background: rgba(0,0,0,0.25);
    border: 1px solid rgba(184, 134, 11, 0.3);
    border-radius: 20px;
    padding: 22px;
    margin-bottom: 22px;
}
.form-section h3 {
    font-family: 'Orbitron', sans-serif;
    color: #ffd700;
    font-size: 13px;
    letter-spacing: 2px;
    margin-bottom: 16px;
    text-transform: uppercase;
    display: flex;
    align-items: center;
    gap: 8px;
}
.form-row {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 12px;
    margin-bottom: 14px;
}
@media (max-width: 600px) { .form-row { grid-template-columns: 1fr; } }

.table-wrapper {
    overflow-x: auto;
    border-radius: 14px;
    border: 1px solid rgba(184, 134, 11, 0.3);
    background: rgba(0,0,0,0.2);
}
table { width: 100%; border-collapse: collapse; font-size: 12px; }
table th {
    background: rgba(0,0,0,0.5);
    padding: 12px;
    text-align: left;
    color: #ffd700;
    font-weight: 700;
    text-transform: uppercase;
    letter-spacing: 1px;
    font-size: 10px;
    border-bottom: 1px solid rgba(184, 134, 11, 0.3);
}
table td {
    padding: 12px;
    border-bottom: 1px solid rgba(255,255,255,0.04);
    color: #ddd;
    font-size: 11px;
}
table tr:last-child td { border-bottom: none; }
table tr:hover { background: rgba(255,215,0,0.03); }
table td .key-text {
    font-family: 'Courier New', monospace;
    color: #ffed4a;
    font-weight: 700;
    font-size: 11px;
}

.badge {
    display: inline-block;
    padding: 3px 9px;
    border-radius: 20px;
    font-size: 9px;
    font-weight: 700;
    letter-spacing: 1px;
    text-transform: uppercase;
}
.badge-active { background: rgba(0,255,136,0.15); color: #00ff88; border: 1px solid #00ff88; }
.badge-expired { background: rgba(255,50,50,0.15); color: #ff6666; border: 1px solid #ff4444; }
.badge-user { background: rgba(100,150,255,0.15); color: #a0c0ff; border: 1px solid #6080dd; }
.badge-admin { background: rgba(255,215,0,0.15); color: #ffd700; border: 1px solid #ffd700; }

.table-controls {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 12px;
    flex-wrap: wrap;
    gap: 10px;
}
.table-controls h3 {
    font-family: 'Orbitron', sans-serif;
    color: #ffd700;
    font-size: 13px;
    letter-spacing: 2px;
}

.stats-bar {
    display: flex;
    gap: 10px;
    margin-bottom: 20px;
    flex-wrap: wrap;
}
.stat-item {
    flex: 1;
    min-width: 110px;
    padding: 14px;
    background: rgba(0,0,0,0.3);
    border: 1px solid rgba(184, 134, 11, 0.3);
    border-radius: 12px;
    text-align: center;
}
.stat-item .label {
    font-size: 9px;
    color: #886666;
    letter-spacing: 1.5px;
    text-transform: uppercase;
}
.stat-item .value {
    font-family: 'Orbitron', sans-serif;
    font-size: 20px;
    color: #ffd700;
    margin-top: 4px;
    font-weight: 700;
}

.footer {
    text-align: center;
    padding: 16px;
    font-size: 10px;
    color: #886666;
    letter-spacing: 1px;
    border-top: 1px solid rgba(184, 134, 11, 0.15);
}

.hint {
    font-size: 10px;
    color: #886666;
    margin-top: 5px;
    font-style: italic;
}
.hint.valid { color: #00ff88; }
.hint.invalid { color: #ff6666; }

.filter-bar {
    display: flex;
    gap: 8px;
    margin-bottom: 14px;
    flex-wrap: wrap;
}
.filter-btn {
    padding: 8px 16px;
    background: rgba(0,0,0,0.3);
    border: 1px solid rgba(184, 134, 11, 0.3);
    border-radius: 20px;
    color: #886666;
    font-size: 11px;
    font-weight: 600;
    cursor: pointer;
    transition: all 0.3s;
    font-family: 'Poppins', sans-serif;
}
.filter-btn:hover { color: #ffd700; border-color: rgba(255,215,0,0.4); }
.filter-btn.active {
    background: linear-gradient(135deg, #8b0000, #cc0000);
    color: #ffed4a;
    border-color: #ffd700;
    box-shadow: 0 4px 15px -3px rgba(139, 0, 0, 0.8);
}
</style>
</head>
<body>

<div class="container">
    <div class="header">
        <h1>🔐 ADMIN KEY PANEL</h1>
        <p>Generate Manual Keys for Users</p>
    </div>

    <div class="info-bar">
        <span>🔒 <strong>Private Access</strong> — Hanya admin</span>
        <span id="clock"></span>
    </div>

    <div class="content">
        
        <div class="alert alert-info show">
            💡 Buat key manual untuk user. <strong>Minimal 3 huruf</strong>, maksimal bebas.
        </div>

        <div class="stats-bar">
            <div class="stat-item">
                <div class="label">Total Keys</div>
                <div class="value" id="statTotal">0</div>
            </div>
            <div class="stat-item">
                <div class="label">Aktif</div>
                <div class="value" id="statActive" style="color:#00ff88;">0</div>
            </div>
            <div class="stat-item">
                <div class="label">Expired</div>
                <div class="value" id="statExpired" style="color:#ff6666;">0</div>
            </div>
        </div>

        <div class="alert alert-error" id="createError"></div>
        <div class="alert alert-success" id="createSuccess"></div>

        <!-- CREATE FORM -->
        <div class="form-section">
            <h3><i class="fas fa-plus-circle"></i> BUAT KEY MANUAL</h3>
            
            <div class="form-group">
                <label class="form-label">Key Value (min. 3 huruf) *</label>
                <input type="text" class="form-input" id="newKeyValue" 
                       placeholder="contoh: VIP2025" 
                       oninput="validateKey(this.value)" maxlength="50"
                       autocomplete="off">
                <div class="hint" id="keyHint">Minimal 3 karakter, huruf & angka</div>
            </div>

            <div class="form-row">
                <div class="form-group">
                    <label class="form-label">Durasi</label>
                    <select class="form-select" id="newKeyDuration">
                        <option value="3">3 Menit (default)</option>
                        <option value="10">10 Menit</option>
                        <option value="30">30 Menit</option>
                        <option value="60">1 Jam</option>
                        <option value="1440">1 Hari</option>
                        <option value="10080">7 Hari</option>
                        <option value="43200">30 Hari</option>
                        <option value="0">∞ Tidak Terbatas</option>
                    </select>
                </div>
                <div class="form-group">
                    <label class="form-label">Untuk User (opsional)</label>
                    <input type="text" class="form-input" id="newKeyFor" placeholder="username target" autocomplete="off">
                </div>
            </div>

            <div class="form-group">
                <label class="form-label">Catatan (opsional)</label>
                <textarea class="form-textarea" id="newKeyNote" placeholder="Catatan admin..."></textarea>
            </div>

            <button class="btn btn-primary" onclick="createManualKey()" id="createBtn">
                <i class="fas fa-key"></i> GENERATE KEY
            </button>
        </div>

        <!-- KEY LIST -->
        <div class="table-controls">
            <h3><i class="fas fa-list"></i> DAFTAR KEY</h3>
            <button class="btn btn-primary btn-sm" onclick="loadKeys()">
                <i class="fas fa-sync"></i> REFRESH
            </button>
        </div>

        <!-- FILTER -->
        <div class="filter-bar">
            <button class="filter-btn active" data-filter="all" onclick="setFilter('all')">
                <i class="fas fa-list"></i> Semua
            </button>
            <button class="filter-btn" data-filter="active" onclick="setFilter('active')">
                <i class="fas fa-check-circle"></i> Aktif
            </button>
            <button class="filter-btn" data-filter="expired" onclick="setFilter('expired')">
                <i class="fas fa-clock"></i> Expired
            </button>
            <button class="filter-btn" data-filter="admin" onclick="setFilter('admin')">
                <i class="fas fa-crown"></i> Admin
            </button>
            <button class="filter-btn" data-filter="user" onclick="setFilter('user')">
                <i class="fas fa-user"></i> User
            </button>
        </div>

        <div class="table-wrapper">
            <table>
                <thead>
                    <tr>
                        <th>ID</th>
                        <th>Key</th>
                        <th>By</th>
                        <th>Status</th>
                        <th>Expired</th>
                        <th>Aksi</th>
                    </tr>
                </thead>
                <tbody id="keyTableBody">
                    <tr><td colspan="6" style="text-align:center; color:#886666; padding:20px;">
                        <i class="fas fa-spinner fa-spin"></i> Loading...
                    </td></tr>
                </tbody>
            </table>
        </div>
    </div>

    <div class="footer">© 2025 AzferModz • Admin Panel</div>
</div>

<script>
// ================================================================
// KONFIGURASI DATABASE
// ================================================================
const DB_API_KEY = "sk_34701ad7da358959a51880e914c5515d6947c583dc37cb90";
const DB_HOST = "https://free-database-fazxy.netlify.app";
const DB_BASE = DB_HOST + "/api/v1";
const KEYS_COLLECTION = "keys";

// ================================================================
// STATE
// ================================================================
let currentKeys = [];
let currentFilter = 'all';

// ================================================================
// CLOCK
// ================================================================
function updateClock() {
    const now = new Date();
    document.getElementById('clock').textContent = 
        now.toLocaleTimeString('id-ID') + ' • ' + 
        now.toLocaleDateString('id-ID', { day:'2-digit', month:'short', year:'numeric' });
}
setInterval(updateClock, 1000);
updateClock();

// ================================================================
// API
// ================================================================
async function apiRequest(method, path, body=null) {
    const url = DB_BASE + path;
    const opts = {
        method,
        headers: {
            'x-api-key': DB_API_KEY,
            'Content-Type': 'application/json',
            'Accept': 'application/json'
        }
    };
    if (body) opts.body = JSON.stringify(body);
    const res = await fetch(url, opts);
    const text = await res.text();
    let data;
    try { data = JSON.parse(text); } catch { data = text; }
    return { ok: res.ok, status: res.status, data };
}

function parseArray(data) {
    if (Array.isArray(data)) return data;
    if (data && Array.isArray(data.data)) return data.data;
    if (data && Array.isArray(data.items)) return data.items;
    return [];
}

function escapeHtml(s) {
    return String(s == null ? '' : s).replace(/[&<>"']/g, c => 
        ({'&':'&amp;','<':'&lt;','>':'&gt;','"':'&quot;',"'":'&#39;'}[c]));
}

function showAlert(id, msg, type='error') {
    const el = document.getElementById(id);
    el.className = 'alert alert-' + type + ' show';
    el.innerHTML = msg;
    setTimeout(() => el.classList.remove('show'), 5000);
}

// ================================================================
// VALIDATE KEY
// ================================================================
function validateKey(value) {
    const hint = document.getElementById('keyHint');
    const cleaned = value.trim();
    
    if (cleaned.length === 0) {
        hint.textContent = 'Minimal 3 karakter, huruf & angka';
        hint.className = 'hint';
        return false;
    }
    if (cleaned.length < 3) {
        hint.textContent = `❌ Kurang ${3 - cleaned.length} karakter lagi`;
        hint.className = 'hint invalid';
        return false;
    }
    if (!/^[A-Za-z0-9_\-]+$/.test(cleaned)) {
        hint.textContent = '❌ Hanya huruf, angka, _ dan -';
        hint.className = 'hint invalid';
        return false;
    }
    hint.textContent = `✅ Valid (${cleaned.length} karakter)`;
    hint.className = 'hint valid';
    return true;
}

// ================================================================
// CREATE MANUAL KEY
// ================================================================
async function createManualKey() {
    const keyValue = document.getElementById('newKeyValue').value.trim();
    const duration = parseInt(document.getElementById('newKeyDuration').value);
    const forUser = document.getElementById('newKeyFor').value.trim();
    const note = document.getElementById('newKeyNote').value.trim();

    // Validasi
    if (!validateKey(keyValue)) {
        showAlert('createError', '❌ Key tidak valid! Minimal 3 huruf.');
        return;
    }

    // Cek duplikat
    const isDuplicate = currentKeys.some(k => 
        String(k.key_value || '').toLowerCase() === keyValue.toLowerCase()
    );
    if (isDuplicate) {
        showAlert('createError', `❌ Key "${keyValue}" sudah ada di database!`);
        return;
    }

    const btn = document.getElementById('createBtn');
    btn.disabled = true;
    btn.innerHTML = '<i class="fas fa-spinner fa-spin"></i> Creating...';

    try {
        const now = new Date();
        const expiresAt = duration === 0
            ? null
            : new Date(now.getTime() + duration * 60 * 1000).toISOString();

        const payload = {
            key_value: keyValue,
            created_by: "admin",
            created_at: now.toISOString(),
            expires_at: expiresAt,
            is_active: true,
            note: (note || "Manual key") + (forUser ? ` | for: ${forUser}` : "")
        };

        const attempts = [
            { method: 'POST', path: `/${KEYS_COLLECTION}` },
            { method: 'POST', path: `/${KEYS_COLLECTION}/create` },
            { method: 'POST', path: `/${KEYS_COLLECTION}/insert` }
        ];

        let success = false;
        let lastRes = null;
        for (const a of attempts) {
            const res = await apiRequest(a.method, a.path, payload);
            lastRes = res;
            if (res.ok) { success = true; break; }
            if (res.status !== 404 && res.status !== 405) break;
        }

        if (!success) throw new Error(`Gagal simpan (status ${lastRes.status})`);

        showAlert('createSuccess', `✅ Key <strong>${escapeHtml(keyValue)}</strong> berhasil dibuat!`, 'success');
        
        // Reset form
        document.getElementById('newKeyValue').value = '';
        document.getElementById('newKeyFor').value = '';
        document.getElementById('newKeyNote').value = '';
        document.getElementById('keyHint').textContent = 'Minimal 3 karakter, huruf & angka';
        document.getElementById('keyHint').className = 'hint';

        loadKeys();

    } catch (err) {
        showAlert('createError', '❌ ' + err.message);
    } finally {
        btn.disabled = false;
        btn.innerHTML = '<i class="fas fa-key"></i> GENERATE KEY';
    }
}

// ================================================================
// FILTER
// ================================================================
function setFilter(filter) {
    currentFilter = filter;
    document.querySelectorAll('.filter-btn').forEach(b => b.classList.remove('active'));
    document.querySelector(`[data-filter="${filter}"]`).classList.add('active');
    renderKeys();
}

// ================================================================
// LOAD KEYS
// ================================================================
async function loadKeys() {
    const tbody = document.getElementById('keyTableBody');
    tbody.innerHTML = `<tr><td colspan="6" style="text-align:center; color:#886666; padding:20px;">
        <i class="fas fa-spinner fa-spin"></i> Loading...
    </td></tr>`;

    try {
        const res = await apiRequest('GET', `/${KEYS_COLLECTION}`);
        if (!res.ok) {
            tbody.innerHTML = `<tr><td colspan="6" style="text-align:center; color:#ff6666; padding:20px;">
                ❌ Status: ${res.status}
            </td></tr>`;
            return;
        }

        const keys = parseArray(res.data);
        currentKeys = keys;

        // Update stats
        const now = Date.now();
        const activeCount = keys.filter(k => {
            if (!k.is_active) return false;
            if (k.expires_at && new Date(k.expires_at).getTime() < now) return false;
            return true;
        }).length;

        document.getElementById('statTotal').textContent = keys.length;
        document.getElementById('statActive').textContent = activeCount;
        document.getElementById('statExpired').textContent = keys.length - activeCount;

        renderKeys();

    } catch (err) {
        tbody.innerHTML = `<tr><td colspan="6" style="text-align:center; color:#ff6666; padding:20px;">
            ❌ ${escapeHtml(err.message)}
        </td></tr>`;
    }
}

// ================================================================
// RENDER KEYS (dengan filter)
// ================================================================
function renderKeys() {
    const tbody = document.getElementById('keyTableBody');
    const now = Date.now();

    // Filter
    let filtered = currentKeys.filter(k => {
        const isExpired = k.expires_at && new Date(k.expires_at).getTime() < now;
        const isActive = k.is_active && !isExpired;
        
        if (currentFilter === 'active') return isActive;
        if (currentFilter === 'expired') return !isActive;
        if (currentFilter === 'admin') return k.created_by === 'admin';
        if (currentFilter === 'user') return k.created_by === 'user' || !k.created_by;
        return true;
    });

    // Sort by created_at desc
    filtered.sort((a, b) => new Date(b.created_at || 0) - new Date(a.created_at || 0));

    if (filtered.length === 0) {
        tbody.innerHTML = `<tr><td colspan="6" style="text-align:center; color:#886666; padding:20px;">
            📭 Tidak ada key${currentFilter !== 'all' ? ' di filter ini' : ''}.
        </td></tr>`;
        return;
    }

    tbody.innerHTML = filtered.map(k => {
        const isExpired = k.expires_at && new Date(k.expires_at).getTime() < now;
        const isActive = k.is_active && !isExpired;
        
        let expiredText = '∞ Never';
        if (k.expires_at) {
            const exp = new Date(k.expires_at);
            const diff = exp.getTime() - now;
            if (diff > 0) {
                const mins = Math.floor(diff / 60000);
                if (mins < 60) expiredText = `⏰ ${mins}m`;
                else if (mins < 1440) expiredText = `⏰ ${Math.floor(mins/60)}h ${mins%60}m`;
                else expiredText = `⏰ ${Math.floor(mins/1440)}d`;
            } else {
                expiredText = '❌ Expired';
            }
        }

        return `<tr>
            <td>${k.id || '-'}</td>
            <td><span class="key-text">${escapeHtml(k.key_value || '-')}</span></td>
            <td><span class="badge badge-${k.created_by === 'admin' ? 'admin' : 'user'}">
                ${escapeHtml(k.created_by || 'user')}
            </span></td>
            <td><span class="badge badge-${isActive ? 'active' : 'expired'}">
                ${isActive ? 'AKTIF' : 'EXPIRED'}
            </span></td>
            <td>${expiredText}</td>
            <td>
                <button class="btn btn-danger" onclick="deleteKey(${k.id}, '${escapeHtml(k.key_value)}')">
                    <i class="fas fa-trash"></i>
                </button>
            </td>
        </tr>`;
    }).join('');
}

// ================================================================
// DELETE KEY
// ================================================================
async function deleteKey(id, keyValue) {
    if (!confirm(`Hapus key "${keyValue}"?`)) return;

    const attempts = [
        { method: 'DELETE', path: `/${KEYS_COLLECTION}/${id}` },
        { method: 'DELETE', path: `/${KEYS_COLLECTION}?id=${id}` },
        { method: 'POST',   path: `/${KEYS_COLLECTION}/delete/${id}` }
    ];

    let success = false;
    let lastRes = null;
    for (const a of attempts) {
        const res = await apiRequest(a.method, a.path);
        lastRes = res;
        if (res.ok) { success = true; break; }
        if (res.status !== 404 && res.status !== 405) break;
    }

    if (success) {
        showAlert('createSuccess', `✅ Key dihapus.`, 'success');
        loadKeys();
    } else {
        showAlert('createError', `❌ Gagal hapus (status ${lastRes.status})`);
    }
}

// ================================================================
// INIT
// ================================================================
window.addEventListener('DOMContentLoaded', () => {
    console.log('%c🔐 Admin Key Panel (Private Mode)', 'color:#ffd700; font-weight:bold; font-size:14px;');
    console.log('%c⚠️ JANGAN SHARE URL INI KE SIAPAPUN!', 'color:#ff4444; font-weight:bold;');
    loadKeys();
});
</script>

</body>
</html>

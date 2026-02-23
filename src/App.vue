<template>
  <div class="layout">
    <!-- Sidebar -->
    <aside class="sidebar">
      <div class="logo">
        <div class="logo-icon">💬</div>
        <div>
          <div class="logo-title">AI Chatbot</div>
          <div class="logo-sub">UBND Phường</div>
        </div>
      </div>

      <div class="menu">
        <div class="menu-section">Kho tri thức</div>
        <div class="menu-item active">Nguồn dữ liệu</div>
        <div class="menu-item">URL Website</div>
        <div class="menu-item">Văn bản thủ công</div>
      </div>
    </aside>

    <!-- Main Content -->
    <main class="content">
      <div class="header">
        <div>
          <h1>Nguồn dữ liệu</h1>
          <p>Quản lý file và tài liệu tri thức</p>
        </div>

        <button class="btn-primary">+ Thêm tài liệu</button>
      </div>

      <!-- Search -->
      <div class="search-box">
        <input type="text" placeholder="Tìm kiếm tài liệu..." />
      </div>

      <!-- Stats -->
      <div class="stats">
        <div class="card">
          <div class="card-label">Tổng tài liệu</div>
          <div class="card-value">85</div>
        </div>

        <div class="card">
          <div class="card-label">Đang hoạt động</div>
          <div class="card-value active">67</div>
        </div>

        <div class="card">
          <div class="card-label">Tổng chunks</div>
          <div class="card-value">1,247</div>
        </div>

        <div class="card">
          <div class="card-label">Dung lượng</div>
          <div class="card-value">128 MB</div>
        </div>
      </div>

      <!-- Table -->
      <div class="table-wrapper">
        <table>
          <thead>
            <tr>
              <th>Tài liệu</th>
              <th>Kích thước</th>
              <th>Chunks</th>
              <th>Trạng thái</th>
              <th>Cập nhật</th>
              <th>Phiên bản</th>
              <th>Thao tác</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="doc in documents" :key="doc.id">
              <td>
                <div class="doc-name">
                  📄 {{ doc.name }}
                  <div class="doc-type">{{ doc.type }}</div>
                </div>
              </td>
              <td>{{ doc.size }}</td>
              <td>
                <span class="badge">{{ doc.chunks }}</span>
              </td>
              <td>
                <span class="status">Đang dùng</span>
              </td>
              <td>{{ doc.updated }}</td>
              <td>{{ doc.version }}</td>
              <td>
                <div class="actions">
                  <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-download w-4 h-4"><path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"></path><polyline points="7 10 12 15 17 10"></polyline><line x1="12" x2="12" y1="15" y2="3"></line></svg>
                </div>
              </td>
            </tr>
          </tbody>
        </table>
      </div>
    </main>
  </div>
</template>

<script setup>
import { ref } from "vue";

const documents = ref([
  {
    id: 1,
    name: "Quy trình đăng ký tạm trú.pdf",
    type: "PDF",
    size: "2.4 MB",
    chunks: 45,
    updated: "2 giờ trước",
    version: "v3",
  },
  {
    id: 2,
    name: "Hướng dẫn thủ tục hành chính.docx",
    type: "DOCX",
    size: "1.8 MB",
    chunks: 32,
    updated: "1 ngày trước",
    version: "v2",
  },
  {
    id: 3,
    name: "Danh sách phí lệ phí.xlsx",
    type: "XLSX",
    size: "512 KB",
    chunks: 12,
    updated: "3 ngày trước",
    version: "v1",
  },
]);
</script>

<style scoped>
.layout {
  display: flex;
  height: 100vh;
  font-family: Arial, sans-serif;
  background: #f5f6fa;
}

/* Sidebar */
.sidebar {
  width: 285px;
  background: white;
  border-right: 1px solid #eee;
  padding: 20px;
}

.logo {
  display: flex;
  align-items: center;
  gap: 10px;
  margin-bottom: 30px;
}

.logo-icon {
  font-size: 24px;
}

.logo-title {
  font-weight: bold;
}

.logo-sub {
  font-size: 12px;
  color: gray;
}

.menu-section {
  font-weight: bold;
  margin-bottom: 10px;
}

.menu-item {
  padding: 8px 10px;
  border-radius: 6px;
  cursor: pointer;
  margin-bottom: 5px;
}

.menu-item:hover {
  background: #f1f3f9;
}

.menu-item.active {
  background: #e8edff;
  color: #3b5bfd;
  font-weight: 600;
}

/* Content */
.content {
  flex: 1;
  padding: 30px;
  overflow-y: auto;
}

.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.header h1 {
  margin: 0;
}

.header p {
  margin: 4px 0 0;
  color: gray;
  font-size: 14px;
}

.btn-primary {
  background: #111827;
  color: white;
  padding: 10px 16px;
  border-radius: 8px;
  border: none;
  cursor: pointer;
}

.search-box {
  margin: 20px 0;
}

.search-box input {
  width: 100%;
  padding: 10px 14px;
  border-radius: 8px;
  border: 1px solid #ddd;
}

/* Stats */
.stats {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 20px;
  margin-bottom: 30px;
}

.card {
  background: white;
  padding: 20px;
  border-radius: 12px;
  box-shadow: 0 2px 6px rgba(0,0,0,0.05);
}

.card-label {
  font-size: 14px;
  color: gray;
}

.card-value {
  font-size: 24px;
  font-weight: bold;
  margin-top: 8px;
}

.card-value.active {
  color: #16a34a;
}

/* Table */
.table-wrapper {
  background: white;
  border-radius: 12px;
  overflow: hidden;
}

table {
  width: 100%;
  border-collapse: collapse;
}

thead {
  background: #f9fafb;
}

th, td {
  padding: 14px;
  text-align: left;
  border-bottom: 1px solid #eee;
}

.badge {
  background: #e9d5ff;
  padding: 4px 10px;
  border-radius: 20px;
  font-size: 12px;
}

.status {
  background: #dcfce7;
  color: #15803d;
  padding: 4px 10px;
  border-radius: 20px;
  font-size: 12px;
}

.doc-type {
  font-size: 12px;
  color: gray;
}

.actions {
  cursor: pointer;
}
</style>

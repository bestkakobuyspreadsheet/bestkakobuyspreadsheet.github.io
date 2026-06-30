<script setup>
import { useData } from 'vitepress'
import LeftSidebar from './LeftSidebar.vue'
import RightSidebar from './RightSidebar.vue'

const { frontmatter } = useData()
</script>

<template>
  <div class="custom-doc-layout">
    <!-- Title bar -->
    <header class="custom-doc-header">
      <h1 v-if="frontmatter.title">{{ frontmatter.title }}</h1>
      <!-- Action buttons below title -->
      <div class="doc-action-buttons">
        <a
          href="https://docs.google.com/spreadsheets/d/1Vs190yOAkrQ04LQb6l_Lnr_oTA0ny4CI3PJ_0B4_6zs/edit?gid=1903531254#gid=1903531254"
          target="_blank"
          rel="noopener noreferrer"
          class="doc-btn doc-btn-primary"
          aria-label="Access Kakobuy Spreadsheet"
        >
          Access Kakobuy Spreadsheet
        </a>
        <a
          href="/platforms/"
          class="doc-btn doc-btn-secondary"
          aria-label="Browse Other Platforms"
        >
          Other Platforms
        </a>
      </div>
    </header>

    <!-- Three-column body -->
    <div class="custom-doc-body">
      <!-- Left sidebar: Brand directory -->
      <LeftSidebar />

      <!-- Main content -->
      <main class="custom-doc-content">
        <Content />
      </main>

      <!-- Right sidebar: Trending deals -->
      <RightSidebar />
    </div>
  </div>
</template>

<style scoped>
.custom-doc-layout {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 1.5rem;
}

/* Header */
.custom-doc-header {
  padding: 2rem 0 1.5rem;
  border-bottom: 1px solid #e0e0e0;
  margin-bottom: 2rem;
}

.dark .custom-doc-header {
  border-bottom-color: #3a3a4e;
}

.custom-doc-header h1 {
  font-size: 2.2rem;
  font-weight: 800;
  color: var(--vp-c-text-1);
  margin: 0 0 1rem;
}

/* Action buttons */
.doc-action-buttons {
  display: flex;
  gap: 0.75rem;
  flex-wrap: wrap;
}

.doc-btn {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  padding: 0.6rem 1.4rem;
  border-radius: 8px;
  font-size: 0.95rem;
  font-weight: 600;
  text-decoration: none;
  transition: all 0.2s ease;
  cursor: pointer;
  border: none;
  line-height: 1.4;
}

.doc-btn-primary {
  background: var(--vp-c-brand-1);
  color: #fff;
}

.doc-btn-primary:hover {
  background: var(--vp-c-brand-2);
  transform: translateY(-1px);
  box-shadow: 0 4px 12px rgba(229, 57, 53, 0.3);
}

.doc-btn-secondary {
  background: transparent;
  color: var(--vp-c-brand-1);
  border: 2px solid var(--vp-c-brand-1);
}

.doc-btn-secondary:hover {
  background: var(--vp-c-brand-1);
  color: #fff;
  transform: translateY(-1px);
}

.doc-btn:focus-visible {
  outline: 2px solid var(--vp-c-brand-1);
  outline-offset: 2px;
}

/* Body: three columns */
.custom-doc-body {
  display: grid;
  grid-template-columns: 220px 1fr 240px;
  gap: 2rem;
  align-items: start;
}

/* Main content */
.custom-doc-content {
  min-width: 0;
}

/* Responsive */
@media (max-width: 768px) {
  .custom-doc-body {
    grid-template-columns: 1fr;
  }

  .custom-doc-header h1 {
    font-size: 1.6rem;
  }

  .doc-btn {
    padding: 0.5rem 1rem;
    font-size: 0.85rem;
  }
}
</style>

<template>
  <teleport to="body">
    <div class="modal-overlay" @click="closeModal">
      <div class="modal-container" @click.stop>
        <p>{{ selectedDate }}</p>
        <div class="radio-container">
          <div
            class="radio-group"
            v-for="(item, index) in radioGroup"
            :key="index"
          >
            <input
              type="radio"
              :value="item.value"
              v-model="newPriority"
              class="radio"
              :id="item.id"
            />
            <label class="radio-label" :for="item.id">{{ item.label }}</label>
          </div>
        </div>
        <input
          v-model="newTitle"
          @keyup.enter="addTodo"
          placeholder="제목을 입력하세요."
          class="input"
        />
        <input
          v-model="newContent"
          @keyup.enter="addTodo"
          placeholder="내용을 입력하세요."
          class="input"
        />
        <button
          class="modal-button"
          @click="addTodo(this.newTitle, this.newContent, this.newPriority)"
        >
          등록하기
        </button>
      </div>
    </div>
  </teleport>
</template>

<script>
import { inject } from "vue";

export default {
  name: "Modal",
  setup() {
    const closeModal = inject("closeModal");
    const selectedDate = inject("selectedDate");
    const initialListItemData = inject("initialListItemData");
    const addTodo = inject("addTodo");

    return { closeModal, selectedDate, initialListItemData, addTodo };
  },
  data() {
    return {
      newTitle: "",
      newContent: "",
      newPriority: "medium",
      radioGroup: [
        {
          id: "priority-high",
          value: "high",
          label: "높음",
        },
        {
          id: "priority-medium",
          value: "medium",
          label: "중간",
        },
        {
          id: "priority-low",
          value: "low",
          label: "낮음",
        },
      ],
    };
  },
};
</script>

<style scoped>
.modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(90, 90, 90, 0.5);
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 9;
}

.modal-container {
  background: white;
  padding: 16px 24px;
  border-radius: var(--border-radius-sm);
  display: flex;
  flex-direction: column;
  gap: 16px;
}

.modal-button {
  background-color: var(--purple-dark);
  color: var(--white);
  padding: 12px 24px;
  width: 100%;
  border-radius: var(--border-radius-sm);
}

.input {
  border: 3px solid var(--purple);
  border-radius: var(--border-radius-sm);
  padding: 12px;
  font-family: "KCC-Ganpan";
  color: var(--purple);
}
.input::placeholder {
  color: var(--gray);
}
.input:focus {
  outline: none;
  border: 3px solid var(--purple-dark);
}

.radio-container {
  display: flex;
  gap: 16px;
}
.radio-group {
  display: flex;
  align-items: center;
  gap: 8px;
}
.radio {
  width: 20px;
  height: 20px;
  border: 3px solid var(--purple);
  border-radius: var(--border-radius-full);
  cursor: pointer;
}
.radio:checked {
  border: 3px solid var(--purple);
  background-color: var(--purple-dark);
}
.radio-label {
  cursor: pointer;
}
</style>

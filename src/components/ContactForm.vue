<template>
  <div class="input-form card card-body mt-3">
    <div class="row g-3">
      <div class="col-md-2">
        <input
          type="text"
          class="form-control"
          placeholder="이름"
          v-model="newContact.name"
        />
      </div>
      <div class="col-md-2">
        <select
          class="form-select"
          placeholder="성별"
          v-model="newContact.gender"
        >
          <option value="">성별</option>
          <option value="남">남</option>
          <option value="여">여</option>
        </select>
      </div>
      <div class="col-md-2">
        <input
          type="number"
          class="form-control"
          placeholder="나이"
          v-model="newContact.age"
        />
      </div>
      <div class="col-md-3">
        <input
          type="email"
          class="form-control"
          placeholder="email"
          v-model="newContact.email"
        />
      </div>
      <div class="col-md-2">
        <input
          type="text"
          class="form-control"
          placeholder="github ID"
          v-model="newContact.github"
        />
      </div>
      <div class="col-md-1">
        <button class="btn btn-primary w-100" @click="$emit('add-form')">
          추가
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    newContact: Object,
  },
  emits: ["add-form"],

  methods: {
    // 이름이 입력 안된 경우 '이름을 입력하세요' 알림창
    // 이메일이 입력 안된 경우 '이메일을 입력하세요' 알림창
    // 둘 다 입력이 된 경우 연락처 추가
  },
};
</script>

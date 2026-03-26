<template>
  <div class="input-form card card-body mt-3">
    <div class="row g-3">
      <div class="col-md-2">
        <input
          type="text"
          class="form-control"
          placeholder="이름"
          v-model="input_arr[0]"
        />
      </div>
      <div class="col-md-2">
        <select class="form-select" placeholder="성별" v-model="input_arr[1]">
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
          v-model="input_arr[2]"
        />
      </div>
      <div class="col-md-3">
        <input
          type="email"
          class="form-control"
          placeholder="email"
          v-model="input_arr[3]"
        />
      </div>
      <div class="col-md-2">
        <input
          type="text"
          class="form-control"
          placeholder="github ID"
          v-model="input_arr[4]"
        />
      </div>
      <div class="col-md-1">
        <button class="btn btn-primary w-100" @click="addFormHandler">
          추가
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ContactForm',

  data() {
    return {
      input_arr: [],
    };
  },
  emits: ['add-form'], //이벤트 이름 명시해주기
  methods: {
    // 이름이 입력 안된 경우 '이름을 입력하세요' 알림창
    // 이메일이 입력 안된 경우 '이메일을 입력하세요' 알림창
    // 둘 다 입력이 된 경우 연락처 추가
    addFormHandler() {
      console.log(this.input_arr); //로그 -> Proxy(Array) {0: '정민규', 1: ~~~~~다 나옴}
      this.$emit('add-form', this.input_arr);
    },
  },
};
</script>

<!-- 구조!

ContactForm.vue에서 버튼 클릭 시 -> addTodoHandler 함수 발생

addFormHandlert() 
{
	이름,이메일 v-model로 받아와서
	if(이름 length && 이메일 length가 둘 다 > 0) 
	{
			
	}
	 else if(이름 length && 이메일 length가 둘 다 0이면)
	{
		alert ~~~~
		return; //끝내기		
	}

	else if(이름 length가 0이면)
	{
		alert ~~~~
		return; //끝내기		
	}
	else if(이메일 length가 0이면)
	{
		alert ~~~~
		return; //끝내기		
	}

}


=> alert는 APP.vue에서 실행해야함.

-->

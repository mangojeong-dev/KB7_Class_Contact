<template>
  <div id="app" class="container-lg">
    <div class="card card-body bg-light">
      <div class="title">우리반 Contact ❤️</div>
    </div>
    <!-- 연락처 입력 폼 -->
    <ContactForm @add-form="addForm" />
    <!-- 연락처 목록 -->
    <ContactList :contacts="contacts" />
  </div>
</template>

<script>
import ContactForm from './components/ContactForm.vue';
import ContactList from './components/ContactList.vue';
export default {
  name: 'App',
  components: { ContactForm, ContactList },

  data() {
    return {
      newContact: {
        name: '',
        gender: '',
        age: '',
        email: '',
        github: '',
      },
      contacts: [
        {
          id: 1,
          name: '홍길동',
          gender: '남',
          age: 20,
          email: 'hong@example.com',
          github: 'hongGD',
          isEditing: false,
        },
        {
          id: 2,
          name: '짱구',
          gender: '남',
          age: 7,
          email: 'janggu@example.com',
          github: 'janggu',
          isEditing: false,
        },
        {
          id: 3,
          name: '유리',
          gender: '여',
          age: 7,
          email: 'yuri@example.com',
          github: 'yuri',
          isEditing: false,
        },
      ],
    };
  },
  methods: {
    /* contact 추가 */
    addForm(arr) {
      console.log(`addForm() 함수 실행 arr: ${arr}`);
      this.contact.name = arr[0];
      this.contact.gender = arr[1];
      this.contact.age = arr[2];
      this.contact.email = arr[3];
      this.contact.github = arr[4];
      if (this.contact.name.length > 0 && this.contact.email.length > 0) {
        console.log(`this.contact.name.length: ${this.contact.name.length} `);
        this.contact.push(arr);
        this.contact.splice(0);
        console.log(
          `입력 배열 비움 - arr[0].length: ${this.contact.name.length}`,
        );
        return;
        //로그 확인 결과 여기까지 정상작동
        // -> 이후 경우의 수는 쭉 작성
      }
      //  else if (arr[0].length === 0 && arr[3].length === 0) {
      //   alert('이름과 이메일 입력하라');
      //   return;
      // } else if (arr[0].length === 0) {
      //   alert('이름을 입력하라');
      //   return;
      // } else if (arr[3].length === 0) {
      //   alert('이메일 입력하라');
      //   return;
      // }
    },

    /* contact 삭제 */
  },
};
</script>

<!-- 
      if (arr[0].length > 0 && arr[3].length > 0) {
        console.log('addTodoHandler() 함수 실행 - 이름,이메일 둘 다 입력됨');
        this.$emit('add-form', arr);
        console.log(
          `arr이 APP.vue로 전달됨. arr: ${arr}`,
        );
        arr.splice(0);
        console.log(`input_arr 배열 비움 - input_arr[0]: ${arr[0]}`);
        return;
        //로그 확인 결과 여기까지 정상작동
        // -> 이후 경우의 수는 쭉 작성
      } else if (
        arr[0].length === 0 &&
        arr[3].length === 0
      ) {
        alert('이름과 이메일 입력하라');
        return;
      } else if (arr[0].length === 0) {
        alert('이름을 입력하라');
        return;
      } else if (arr[3].length === 0) {
        alert('이메일 입력하라');
        return;
      }



-->

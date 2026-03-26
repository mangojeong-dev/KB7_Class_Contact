<template>
  <div id="app" class="container-lg">
    <div class="card card-body bg-light">
      <div class="title">우리반 Contact ❤️</div>
    </div>
    <!-- 연락처 입력 폼 -->
    <ContactForm :new-contact="newContact" @add-form="addForm" />
    <!-- 연락처 목록 -->
    <ContactList :contacts="contacts" @delete-contact="deleteContact" />
  </div>
</template>

<script>
import ContactForm from "./components/ContactForm.vue";
import ContactList from "./components/ContactList.vue";
export default {
  name: "App",
  components: { ContactForm, ContactList },

  data() {
    return {
      newContact: {
        name: "",
        gender: "",
        age: "",
        email: "",
        github: "",
      },
      contacts: [
        {
          id: 1,
          name: "홍길동",
          gender: "남",
          age: 20,
          email: "hong@example.com",
          github: "hongGD",
          isEditing: false,
        },
        {
          id: 2,
          name: "짱구",
          gender: "남",
          age: 7,
          email: "janggu@example.com",
          github: "janggu",
          isEditing: false,
        },
        {
          id: 3,
          name: "유리",
          gender: "여",
          age: 7,
          email: "yuri@example.com",
          github: "yuri",
          isEditing: false,
        },
      ],
    };
  },
  methods: {
    /* contact 추가 */
    addForm() {
      console.log("추가 버튼 클릭");
      console.log("현재 입력값(this.newContact):", this.newContact);
      if (!this.newContact.name && !this.newContact.email) {
        alert("이름과 이메일을 입력해야 합니다");
        return;
      }

      if (!this.newContact.name) {
        alert("이름을 입력해야 합니다");
        return;
      }

      if (!this.newContact.email) {
        alert("이메일을 입력해야 합니다");
        return;
      }
      console.log("검증 통과");
      //return; 해놔서 굳이 else if 안 씀

      this.contacts.push({
        id: Date.now(),
        name: this.newContact.name,
        gender: this.newContact.gender,
        age: this.newContact.age,
        email: this.newContact.email,
        github: this.newContact.github,
        isEditing: false,
      });
      console.log("현재 contacts:", this.newContact);

      //초기화
      this.newContact.name = "";
      this.newContact.gender = "";
      this.newContact.age = "";
      this.newContact.email = "";
      this.newContact.github = "";
    },
    /* contact 삭제 */
    deleteContact(id) {
      console.log("삭제 버튼 클릭:", this.contacts);
      const i = this.contacts.findIndex((contact) => contact.id === id);
      if (i == -1) {
        return; //바로 종료
      }
      this.contacts.splice(i, 1);
    },
  },
};
</script>

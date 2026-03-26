<template>
  <tr>
    <td>{{ ContactItem.name }}</td>
    <td>{{ ContactItem.gender }}</td>
    <td>{{ ContactItem.age }}</td>
    <td>{{ ContactItem.email }}</td>
    <td>{{ ContactItem.github }}</td>
    <td>
      <button class="btn btn-danger btn-sm">삭제</button>
    </td>
  </tr>
</template>

<script>
export default {
  name: 'ContactItem',
  props: ['ContactItem'],
};
</script>

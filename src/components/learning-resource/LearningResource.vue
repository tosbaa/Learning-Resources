<template>
  <li>
    <div>
      <header>
        <h3>{{ title }}</h3>
        <button>Delete</button>
      </header>
    </div>
    <p>{{ Description }}</p>
    <nav>
      <a :href="link">View Resource</a>
    </nav>
  </li>
</template>

<script>
export default {
  props: {
    title: {
      type: String,
      required: true,
      default: "Learning Resource Title",
    },
    description: {
      type: String,
      required: true,
      default: "Learning Resource Description",
    },
    link: {
      type: String,
      required: true,
      defualt: "about:blank",
    },
  },
};
</script>
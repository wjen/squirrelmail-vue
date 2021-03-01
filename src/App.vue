<template>
  <h1>VMail Inbox</h1>

  <Suspense>
    <template #default>
      <MailTable />
    </template>
    <template #fallback>
      Loading...
    </template>
  </Suspense>
</template>

<script>
import MailTable from "@/components/MailTable.vue";
export default {
  name: "App",
  components: {
    MailTable
  }
};
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  max-width: 1000px;
  margin: 0 auto;
}
/* Global Styles */

.clickable {
  cursor: pointer;
}

/* Mail Table */
.mail-table {
  border-collapse: collapse;

  tr {
    height: 40px;

    &.read {
      background-color: #eee;
    }
    &:first-of-type td {
      border-top: 1px solid black;
    }
  }

  td {
    border-bottom: 1px solid black;
    padding: 5px;
    text-align: left;

    p {
      max-height: 1.2em;
      overflow-y: hidden;
      margin: 0;
    }

    &.date {
      width: 120px;
    }
  }
}
/* Modal */
.modal,
.overlay {
  width: 100%;
  height: 100%;
  position: fixed;
  left: 0;
  top: 0;
}
.overlay {
  opacity: 0.5;
  background-color: black;
}
.modal-card {
  position: relative;
  max-width: 80%;
  margin: auto;
  margin-top: 30px;
  padding: 20px;
  background-color: white;
  min-height: 500px;
  z-index: 10;
  // opacity: 1;
}

/* Email Modal */
.email-display {
  text-align: left;
}
</style>

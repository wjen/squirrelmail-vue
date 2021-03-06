<template>
  <h1 class="title">SquirrelMail Inbox</h1>

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
import useEmailSelection from "@/composables/use-email-selection";

export default {
  name: "App",
  components: {
    MailTable
  },
  setup() {
    return {
      emailSelection: useEmailSelection()
    };
  }
};
</script>

<style lang="scss">
/* Global Styles */

body {
  --text-color: #222;
  --bkg-color: #fff;
  --anchor-color: #0033cc;
  --read-color: #8f8b8b;
  --modal-color: #fff;
  --border-color: #222;
}
body.dark-theme {
  --text-color: #eee;
  --bkg-color: #121212;
  --read-color: #8f8b8b;
  --anchor-color: #809fff;
  --modal-color: #2c3e50;
  --border-color: #eee;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: var(--text-color);
  margin-top: 60px;
  max-width: 1000px;
  margin: 0 auto;
}
body {
  color: var(--text-color);
  background: var(--bkg-color);
}
a {
  color: var(--anchor-color);
}
div.modal-card {
  background: var(--modal-color);
}

.title {
  font-family: "Libre Baskerville", serif;
}
button {
  font-size: 16px;
  padding: 8px;
  border-radius: 3px;
  margin: 5px 10px 5px 0px;
  cursor: pointer;

  &:disabled {
    cursor: auto;
  }

  &.selected {
    cursor: auto;
    color: black;
    border-color: var(--border-color);
    border-width: 2px;
  }
}

.clickable {
  cursor: pointer;
}

input[type="checkbox"] {
  -webkit-appearance: none;
  cursor: pointer;
  width: 24px;
  height: 24px;
  background: white;
  border-radius: 2px;
  border: 1px solid var(--border-color);
  position: relative;
  vertical-align: middle;
  padding: 10px;

  &.partial-check {
    background: #abc;
  }

  &:checked {
    background: #679;
  }
}

.mb-0 {
  margin-bottom: 0;
}

/* Mail Table */
.mail-table {
  border-collapse: collapse;

  tr {
    height: 40px;

    &.read {
      background-color: var(--read-color);
    }
    &:first-of-type td {
      border-top: 1px solid var(--border-color);
    }
  }

  td {
    border-bottom: 1px solid var(--border-color);
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
  opacity: 1;
}

/* Email Modal */
.email-display {
  text-align: left;
}

/* Bulk Action Bar */
.bulk-action-bar {
  width: 100%;
  max-width: 1000px;
  margin: auto;
  text-align: left;
  padding-bottom: 8px;

  input {
    margin: 5px;
  }

  .checkbox {
    margin-right: 6px;
    margin-left: 3px;
  }
}
</style>

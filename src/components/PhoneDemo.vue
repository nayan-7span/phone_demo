<script>
import { Field, Form, ErrorMessage } from "vee-validate";
import * as yup from "yup";

export default {
  name: "PhoneDemo",
  components: {
    Field,
    Form,
    ErrorMessage,
  },
  data() {
    return {
      phone: "",
    };
  },
  computed: {
    schema() {
      return yup.object({
        mobile: yup
          .string()
          .matches(/^[0-9]+$/, "Must be only digits")
          .required("Please enter mobile number.")
          .length(10, "Mobile number should be 10 digits."),
      });
    },
  },
};
</script>

<template>
  <div class="parent">
    <div class="container">

      <Form :validation-schema="schema" @submit.prevent="" class="phone-form">
        <div class="phone-form">
          <Field
            class="phone-num"
            type="number"
            name="mobile"
            placeholder="Mobile number"
            onkeypress="return /[0-9]/i.test(event.key)"
            required
          />
          <ErrorMessage class="error-msg" name="mobile" />
          <button class="submit-btn">Submit</button>
        </div>
      </Form>

    </div>
  </div>
</template>

<style  scoped>
* {
  margin: 0;
  padding: 0;
}
.parent {
  width: 100%;
  height: 550px;
  display: flex;
  align-items: center;
  justify-content: center;
}
.container {
  padding: 20px;
  background-color: rgb(255, 255, 255);
  box-shadow: 2px 8px 20px gray;
  border-radius: 5px;
}

.phone-num {
  margin: 2px;
  padding: 10px;
}

.phone-form {
  display: flex;
  flex-direction: column;
  width: 250px;
}

.submit-btn {
  margin: 2px;
  padding: 8px;
  background-color: rgb(56, 56, 56);
  font-weight: bold;
  color: white;
  font-size: 17px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

.submit-btn:hover {
  background-color: rgb(27, 27, 27);
}

/* Chrome, Safari, Edge, Opera */
input::-webkit-outer-spin-button,
input::-webkit-inner-spin-button {
  -webkit-appearance: none;
  margin: 0;
}

/* Firefox */
input[type="number"] {
  -moz-appearance: textfield;
}
.error-msg{
    font-size: 15px;
    margin-bottom: 10px;
    margin-left: 2px;
    font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
    color: red;
}
</style>
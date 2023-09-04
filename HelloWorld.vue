<template>
  <div class="Apple" @mouseover="hover = true" @mouseout="hover = false">
    <div class="Apple Events">
      <h3>{{ event.title }}</h3>
      <p class="description">{{ event.description }}</p>
      <div class="extra-details">
        <p><strong>Instructor: </strong> {{ event.instructor }}</p>
        <p><strong>Duration: </strong> {{ event.duration }}</p>
        <p><strong>Price: </strong> {{ event.price }}</p>
        <p><strong>Date: </strong>{{ event.date }}</p>
        <button class="enroll-button" @click="enroll">Add to your calendar</button>
        <div class="contact-us">
          <button class="contact-us" @click="showInput = true">Contact us</button>
          <div class="contact-modal" v-if="showInput">
            <input v-model="userMessage" type="text" placeholder="Type your message..."/>
            <button @click="send">Send</button>
            <button @click="closeInput">Close</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    event: {
      type: Object,
      required: true,
      default: () => ({
        title: 'Think Different',
        description: 'Innovation at every step.',
        instructor: 'Tim Cook',
        duration: '2 hrs',
        price: 'Free',
        date: '13/09/2023 Wednesday 3am AEST.'
      }),
    },
  },
  data() {
    return {
      hover: false,
      userMessage: '',
      showInput: false,
    };
  },
  methods: {
    enroll() {
      alert('2023 Apple Event ' + this.event.title + ' has been added to your calendar. ');
    },
    send() {
      alert('Message sent: ' + this.userMessage);
      this.closeInput();
    },
    closeInput() {
      this.userMessage = '';
      this.showInput = false;
    },
  },
};
</script>

<style>
body {
  background: radial-gradient(circle, rgb(255, 255, 255), rgb(0, 0, 0));
}

.contact-modal {
  display: flex;
  flex-direction: column;
  align-items: center;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(50, 50);
  background-color: white;
  padding: 16px;
  border: 1px solid #ccc;
  border-radius: 4px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.2);
}

.contact-modal input {
  margin: 20px 0;
  padding: 8px;
}

.send-button, .close-button {
  background-color: #3498db;
  color: white;
  border: none;
  padding: 8px 16px;
  border-radius: 4px;
  cursor: pointer;
  margin-top: 8px;
}

</style>

<style scoped>
h3 {
  color: #333;
  font-size: 24px;
  margin-bottom: 8px;
}
.description {
  color: #666;
  font-size: 16px;
  margin-bottom: 16px;
  text-align: center;
}
.extra-details {
  flex-direction: column;
  align-items: flex-start;
  text-align: center;
}
button.enroll-button {
  background-color: #3498db;
  color: white;
  border: none;
  padding: 8px 16px;
  border-radius: 4px;
  cursor: pointer;
  transition: background-color 0.3s ease;
  margin-top: 16px;
}
button.contact-us {
  background-color: #3498db;
  color: white;
  border: none;
  padding: 8px 16px;
  border-radius: 4px;
  cursor: pointer;
  transition: background-color 0.3s ease;
  margin-top: 16px;
}
button.enroll-button:hover {
  background-color: #0077b6;
}
button.contact-us:hover {
  background-color: #0077b6;
}

</style>

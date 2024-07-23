<template>
  <div class="concept">
    <h2>Concept of the Day</h2>
    <p> {{ selectedConcept }}</p>
  </div>

</template>
<script>
export default {
  data() {
    return {
      //the array 
      concepts: [
        'Concept of the Sunday : What is polymorphism, and how is it supported in the coding language of your choice? Sample answer: "Polymorphism can take a few different forms, but generally, it means that an object, code or operation behaves differently in different settings. C++ supports compiler time polymorphism and run time polymorphism. Compiler time polymorphism is when the compiler knows which function to use when making a polymorphic call. Run time polymorphism is when virtual functions are called by type of object referenced."',
        'Concept of the Monday : What is data abstraction? Sample answer: "Data abstraction is a programming concept that refers to the process of hiding the complexity of data by exposing only essential features to the user. It involves separating the logical view of data from its physical implementation, allowing users to interact with the data at a higher level of abstraction without needing to know the details of how it is implemented.An example of data abstraction in action is a simple bank account application. The user interacts with the application through a simple interface that allows them to view their account balance, deposit or withdraw funds, and view transaction history. Behind the scenes, the application uses a more complex data model to store and manage the account data, but this complexity is hidden from the user. The interface provides a simple and easy-to-use abstraction of the underlying data, allowing the user to interact with the application at a higher level of abstraction."',
        'Concept of the Tuesday : What is object-oriented programming (OOP)? Sample answer: "There are many benefits to using OOP over other programming styles. For your company, two of the major benefits would be the simplicity of the programming and the ease of modification. OOP is simpler than other styles of programming because the objects within the program are modeled on real-world objects. The structure of the program is clear and easy to modify because the objects are maintained independently."',
        'Concept of the Wednesday : What is data abstraction? Sample answer: “Data abstraction is a programming concept that refers to the process of hiding the complexity of data by exposing only essential features to the user. It involves separating the logical view of data from its physical implementation, allowing users to interact with the data at a higher level of abstraction without needing to know the details of how it is implemented. An example of data abstraction in action is a simple bank account application. The user interacts with the application through a simple interface that allows them to view their account balance, deposit or withdraw funds, and view transaction history. Behind the scenes, the application uses a more complex data model to store and manage the account data, but this complexity is hidden from the user. The interface provides a simple and easy-to-use abstraction of the underlying data, allowing the user to interact with the application at a higher level of abstraction.”',
        'Concept of the Thursday : Describe two differences between procedural programming and OOP. Sample answer: "The main difference between procedural programming and object-oriented programming is the basis of the language each program uses. Procedural programming uses function-based language, while object-oriented programming uses language based on real-world objects." Please note that none of the companies mentioned in this article are affiliated with Indeed. ',
        'Concept of the Friday : Explain the difference between class and structure. Sample answer: “In a class, data and behavior are encapsulated together, and objects are created from the class. The behavior of an object is implemented using methods to access and manipulate the data stored in the object’s properties. Classes can also inherit from other classes, allowing them to reuse and extend existing code. On the other hand, a structure is a simple data structure that is used to hold a collection of related data but does not have any behavior. Structures can be useful for representing simple data types, such as coordinates, points or other value types. One key difference between classes and structures is that classes are reference types, while structures are value types.”',
        'Concept of the Saturday : What limitations does OOP have? Sample answer: "It’s important to be aware of the limitations of OOP before programming something new. OOP isn’t generally ideal for small problems, but it’s great for large projects. It also takes a lot of upfront planning to make sure everything works correctly once coded. For this reason, it can take longer to do than procedural programming."',
      ],
      selectedConcept: '',
    };
    // source of the questions and answers is :https://www.indeed.com/career-advice/interviewing/object-oriented-programming-interview-questions#:~:text=Here%20are%20a%20few%20knowledge-specific%20questions%20with%20sample,Describe%20two%20differences%20between%20procedural%20programming%20and%20OOP.
  },
  mounted() {
    const currentDay = new Date().getDay();

    this.selectedConcept = this.concepts[currentDay % this.concepts.length];
  }
};
</script>
<style scoped>
.concept {
  text-align: center;
  margin-top: 20px;
  font-size: 18px;
  color: #ffffff;
}
</style>
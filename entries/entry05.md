# Entry 5
##### 4/24/2022

### Progress
Though out the spring break, I collaborated with my partner Andy and had finished the MVP for our project. The source I used during the learning process is the official guide from the firebase document of [Authantication with password and email](https://firebase.google.com/docs/auth/android/password-auth), [Cloud Firestore](https://firebase.google.com/docs/firestore), and Stack Overflow(for the solution to bugs).

#### Firebase Authentication
###### Initializes 
Before access to the authentication system, we need to get the instance of the FirebaseAuth object.
```java
private FirebaseAuth mAuth;
// ...
// Initialize Firebase Auth
mAuth = FirebaseAuth.getInstance();
```
###### Checking authantication status
In our android app, the user will remain login even though they close the app.
In this case, the app will need to determine if user are still login and which user is logged in-
```java
    @Override
    protected void onStart() {
        super.onStart();
        FirebaseUser user = mAuth.getCurrentUser();
        if(user==null){
            startActivity(new Intent(getApplicationContext(),  LoginPage.class));
        } else {
            startActivity(new Intent(MainActivity.this, Main_Page.class));
        }
    }
```
Current user information will be stored in the user object in FirebaseUser classes and using an if statement to determine if the user is null (user will be null if no user is logged in) if the user is null, bring the user to the login page, else the user will be brought to home page.


###### Create account
```java
    EditText newUsername = findViewById(R.id.newUsername);
    EditText newPassword = findViewById(R.id.newPassword);
    String email = newUsername.getText().toString();
    String password = newPassword.getText().toString();
mAuth.createUserWithEmailAndPassword(email,password).addOnCompleteListener(new OnCompleteListener<AuthResult>() {
    @Override
    public void onComplete(@NonNull Task<AuthResult> task) {
        if(task.isSuccessful()){
            //update userinformation to the database
            Map<String, Object> user = new HashMap<>();
            user.put("email",email);
            user.put("password",password);
            user.put("username","visitor");
            user.put("school","");
            Toast.makeText(CreateAccount.this, "User registered successfully", Toast.LENGTH_SHORT).show();
            db.collection("User").document(email).set(user);
            startActivity(new Intent(CreateAccount.this,Main_Page.class));
        } else {
            Toast.makeText(CreateAccount.this, "Registration Error: " + task.getException().getMessage(), Toast.LENGTH_SHORT).show();
        }
    }
});
```
```.createUserWithEmailAndPassWord(String email, String password)``` will create a new account base on the email and password provided in the authentication server in the firebase console, and using ```.addOnCompleteListener()``` we can set the action after the user successfully create an account and the action if they failed to create an account.

###### Login
```java
EditText loginusername = (EditText) findViewById(R.id.username);
EditText loginpassword = (EditText) findViewById(R.id.password);
String email = loginusername.getText().toString();
String password = loginpassword.getText().toString();
mAuth.signInWithEmailAndPassword(email,password).addOnCompleteListener(new OnCompleteListener<AuthResult>() {
    @Override
    public void onComplete(@NonNull Task<AuthResult> task) {
        if (task.isSuccessful()){
            Toast.makeText(LoginPage.this, "User Logged in successfully", Toast.LENGTH_SHORT).show();
            startActivity(new Intent(getApplicationContext(),Main_Page.class));
        }else{
            Toast.makeText(LoginPage.this, "Log in Error: " + task.getException().getMessage(), Toast.LENGTH_SHORT).show();
        }
    }
});
```
The login method is kind of similar to the create account method, but instead of the user object in the firebase server, ```.signInWithEmailAndPassword(String email, String password)``` actually check if the user with the correct email and password passed in exists in the database and update the authentication status if the user exists.
```.addOnCompleteListener()``` can be applied to ```.signInWithEmailAndPassword(String email, String password)``` to set action after user login.

### Engineering Design Process
Now I and my partner are on the 7 steps of the Engineering Design Process, Improving as needed, and getting our way to the final product. Even though we reached the MVP, there are still small parts of our project that can be improved to give users a better-enhanced user experience.

### Skills
The skills me and my partner use is collaboration, google, and problem decomposition. I have to say coding in the android studio is not easy, both I and my partner are building projects while learning java and android studio, and we have encountered lots of problems in android studio. We decided to break the problem piece to piece and distribute the work equally so we can work more efficiently.






[Previous](entry04.md) | [Next](entry06.md)

[Home](../README.md)
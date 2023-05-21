---
title: "SHA, AS IF! Secure Hash Algorithm"
date: 2023-5-21T11:30:03+00:00
weight: 4
# aliases: ["/first"]
tags: []
author: "Chris"
# author: ["Me", "You"] # multiple authors
showToc: true
TocOpen: false
draft: false
hidemeta: false
comments: false
description: "SHA, Secure Hash Algorithm"
canonicalURL: "https://canonical.url/to/page"
disableHLJS: true # to disable highlightjs
disableShare: false
disableHLJS: false
hideSummary: false
searchHidden: true
ShowReadingTime: true
ShowBreadCrumbs: true
ShowPostNavLinks: true
ShowWordCount: true
ShowRssButtonInSectionTermList: true
UseHugoToc: true
cover:
    image: "images/sha.jpg" # image path/url
    alt: "<alt text>" # alt text
    caption: "<text>" # display caption under cover
    relative: false # when using page bundles set this to true
    hidden: true # only hide on current single page

---
## What is SHA (Secure Hash Algorithm)? 

A secure hash algorithm is a mathematical function that takes input data and produces a fixed-size string of characters called a hash value or hash code. The purpose of a secure hash algorithm is to ensure data integrity and provide a way to uniquely identify data.

Here's how it works:

First, a user provides input data (text, files, etc.) that they want to hash. Then the secure hash algorithm applies a series of mathematical operations (via a hash function) to the input data. These operations transform the data into a unique, fixed-length string of  alphanumeric characters, regardless of the input's size.


A secure hash algorithm should produce a unique hash value for each unique input. Even a small change in the input data should result in a significantly different hash value. It is computationally infeasible to derive the original input data from the hash value. This property ensures that the hash value cannot be reverse-engineered to obtain the original data.

Secure hash algorithms, such as MD5 (Message Digest Algorithm 5), SHA-1 (Secure Hash Algorithm 1), and SHA-256 (Secure Hash Algorithm 256-bit), are commonly used in various applications, including data integrity checks, password storage, digital signatures, and data verification. They provide a way to verify the integrity and authenticity of data without revealing the original data itself.



{{< rawhtml >}}
<html>
<head>
<style>
  form {
    max-width: 400px;
    margin: 40px auto;
    padding: 20px;
    background-color: #ffffff;
    border-radius: 8px;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  }
  
  label {
    display: block;
    margin-bottom: 8px;
  }
  
  input[type="password"] {
    width: 100%;
    padding: 10px;
    border: 1px solid #ccc;
    border-radius: 4px;
    box-sizing: border-box;
  }
  
  button[type="submit"] {
    display: block;
    width: 100%;
    padding: 10px;
    margin-top: 16px;
    background-color: #000000;
    color: #ffffff;
    border: none;
    border-radius: 4px;
    cursor: pointer;
  }

  #text-input {
    color: #000000;
    width: 100%;
    padding: 10px;
    border: 1px solid #ccc;
    border-radius: 4px;
    box-sizing: border-box;
    font-size: 14px;
  }
  #verification-result {
    text-align: center;
  }
</style>

<script src="https://cdnjs.cloudflare.com/ajax/libs/crypto-js/4.0.0/crypto-js.min.js"></script>
</head>
<body>
<h1>SHA Hash Generator</h1>
  <p>Input text to generate a hash with MD5, SHA-1, and SHA-256.</p>

<form id="hash-form">
  <label for="text-input">Enter Text:</label>
  <input type="text" id="text-input" required>
  <button type="submit">Generate Hash</button>
</form>
<div id="hash-container"></div>

<h1>Password Verification</h1>
  <p>
  When storing passwords, <strong>DO NOT</strong> store them in plain text. Instead, passwords are typically hashed using a secure hash function like SHA. When a user enters their password for authentication, it is hashed and compared against the stored hash to validate their identity without exposing the actual password.
    <br>
    <br>
  Let's mock this out below, 
  input the same text you did above and see if it gives the correct signature.
  We're using the hash algorithm (SHA-256)to generate a 256-bit(32 byte) "signature" and checking if it matches the same signature you entered above.
  <br><strong>Note: </strong>If you refreshed the browser, generate a new hash.
</p>

<form id="verification-form">
  <label for="password-input">Enter Password:</label>
  <input type="password" id="password-input" required>
  <button type="submit">Verify</button>
</form>
<div id="verification-result"></div>

<script>
   const hashForm = document.getElementById('hash-form');
    const textInput = document.getElementById('text-input');
    const hashContainer = document.getElementById('hash-container');
  
    const verificationForm = document.getElementById('verification-form');
    const passwordInput = document.getElementById('password-input');
    
    let hash = null; // Declare the hash variable outside the event listener
  
    hashForm.addEventListener('submit', event => {
      event.preventDefault();
  
      const text = textInput.value;
  
      // Generate the SHA-256 hash
      hash = CryptoJS.SHA256(text).toString();
      const md5 = CryptoJS.MD5(text).toString();
      const sha1 = CryptoJS.SHA1(text).toString();
      
        
      // Display the hash
      hashContainer.innerHTML = `
        <p>Input Text: ${text}</p>
        <p>MD5 Hash: ${md5}</p>
        <p>SHA-1 Hash: ${sha1}</p>
        <p>SHA-256 Hash: ${hash}</p> 
      `;
  
      // Clear the input field
      textInput.value = '';
    });
    
    verificationForm.addEventListener('submit', event => {
      event.preventDefault();
        
      const enteredPassword = passwordInput.value;
  
      // Define the correct password hash
      const correctPasswordHash = hash; //'a665a45920422f9d417e4867efdc4fb8a04a1f3fff1fa07e998e86f7f7a27ae3'; // Replace with your desired password hash
  
      // Generate the SHA-256 hash of the entered password
      const enteredPasswordHash = CryptoJS.SHA256(enteredPassword).toString();
  
      if (enteredPasswordHash === correctPasswordHash) {
        alert('Password is correct! Access granted.');
      } else {
        alert('Incorrect password. Access denied.');
      }
  
      // Clear the input field
      passwordInput.value = '';
    });
</script>
</body>
</html>
{{< /rawhtml >}}



SHA algorithms, such as SHA-1 and SHA-256, were __not__ designed specifically for password storage. While they are cryptographic hash functions and can be used for password hashing, they have certain limitations that make them less suitable for this purpose. Here are a few reasons why SHA alone is not considered secure for password storage:

1. Speed: SHA algorithms are designed to be fast and efficient, which is desirable for many use cases. However, this speed makes them vulnerable to brute-force and dictionary attacks. Attackers can quickly hash a large number of possible passwords and compare them to the stored hashes, potentially revealing the original passwords.

2. Lack of Salt: A salt is a random value added to the password before hashing, making each password hash unique. SHA algorithms do not inherently include a salt. Without a salt, attackers can use precomputed tables (rainbow tables) to expedite the process of cracking hashed passwords.

3. Lack of Iteration/Key Stretching: Iteration or key stretching is the process of applying the hash function multiple times, which significantly slows down the hashing process. This makes it more difficult and time-consuming for attackers to try different password combinations. SHA algorithms do not provide built-in support for iteration or key stretching.

To address these limitations, it is recommended to use specialized password hashing algorithms designed for secure password storage. Examples of such algorithms include bcrypt, scrypt, and Argon2. These algorithms incorporate features like salting, iteration, and a slower hashing process to make it more difficult and time-consuming for attackers to crack passwords.

By using a dedicated password hashing algorithm, you can enhance the security of password storage and protect against common password-related attacks.


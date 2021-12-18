Exercise 1: Form validation
Hypothesis: Adding form validation to the "name" and "message" fields of the email form will increase form submissions.

Device type: Desktop only

URL: https://surefoot.me/engineer-application-sandbox-v1/

Dev notes:
In my code, I am attaching something that will "listen" to an some event triggered by the user. Once that event is triggered, a series of checks will be performed to determine of the form passed validation. If not, the user will be displayed a message on what to do next. If it passes validation, the form will be submitted.

Currently, the form only checks for a valid email.
Please execute your code on DOM ready and use javascript to handle validation.
Styling/layout of error messaging is up to you.
Include a few lines of a README-esque description that explains your code to a non-technical person.
Your code here:

/* Form Validation Code */

//Get some references to elements of interest so I dont have to traverse the DOM every single time
let form = document.querySelector('form.wpcf7-form.eng-sandbox-form');
let nameInput = document.querySelector('input.wpcf7-form-control.wpcf7-text');
let messageInput = document.querySelector('textarea.wpcf7-form-control.wpcf7-textarea');
let emailInput = document.querySelector('input.wpcf7-form-control.wpcf7-text.wpcf7-email.wpcf7-validates-as-required.wpcf7-validates-as-email');
let submitButton = document.querySelector('input.wpcf7-form-control.has-spinner.wpcf7-submit');

//Add a keypress event listener to the form. I want to beat the current event listener.
form.addEventListener('keypress', e => {
    //If the key thats was pressed was the enter key (form submit) do something
    if(e.keyCode === 13) {
        //Series of checks for input fields displaying various messages depending on which input is blank, and also prevent the default behaviour of form.
        if(nameInput.value === '' && messageInput.value === "" && emailInput.value === "") {
            alert(`You need to fill out all fields`);
            e.preventDefault();
        } else if(nameInput.value === '') {
            alert(`You got a name don't ya!?!?`);
            e.preventDefault();
        } else if(messageInput.value === "") {
            alert(`Hey I think you missed something!`);
            e.preventDefault();
        } else if (emailInput.value === "") {
            alert(`Please enter a email!`);
            e.preventDefault();
        }
    }
});

//Add click listener to button as well to handle that form of submission
submitButton.addEventListener('click', e => {
        //Series of checks again for input fields displaying various messages depending on which input is blank, and also prevent the default behaviour of form.
        if(nameInput.value === '' && messageInput.value === "" && emailInput.value === "") {
            alert(`You need to fill out all fields`);
            e.preventDefault();
        } else if(nameInput.value === '') {
            alert(`You got a name don't ya!?!?`);
            e.preventDefault();
        } else if(messageInput.value === "") {
            alert(`Hey I think you missed something!`);
            e.preventDefault();
        } else if (emailInput.value === "") {
            alert(`Please enter a email!`);
            e.preventDefault();
        }
});

/* End of Form Validation Code */

Exercise 2: Form restyling
Hypothesis: Swapping the position of the two forms and restyling the email form will increase email form submissions.

Device type: Desktop only

URL: https://surefoot.me/engineer-application-sandbox-v1/

Mockup: https://goo.gl/oMM3Pe

Dev notes:
Essentially all we are doing here is changing the styling of certain elements on the page. For starters, we are flipping the positions of the "schedule a call" and email forms. Then we are making adjustments to text content, and positioning of elements such as the "schedule your call now" button. Additionally, the layout of the form is slightly different. I reemoved the labels and added some placeholder text to give the user some indication as to whats needed. I felt the best way to accomplish this was to add a new from to the webpage. Lastly I adjusted the width and location of the form submit button.

Swap the positions of the "schedule a call" and email forms.
Restyle the form to resemble the mockup but don't worry too much about pixel perfection.
Include a few lines of a README-esque description that explains your code to a non-technical person.
Your code here:
/* Form Restyling Code */

//Flip postion of form and schedule a call section
document.querySelector('.vc_col-sm-6.vc_column.column_container.with_padding.vc_custom_1502143926610.vc_custom_1502143926610').style.float = 'right';

//change text above form
document.querySelectorAll('h2.vc_custom_heading')[1].innerText = 'or shoot use an email';

//change text above schedule a call section
document.querySelectorAll('h2.vc_custom_heading')[2].innerText = 'schedule a call';

//style the button
document.querySelector('.textbar.style_2 .btn-bt').style.float = 'right';
document.querySelector('.textbar.style_2 .btn-bt').style.left = '150px';
document.querySelector('.textbar.style_2 .btn-bt').style.position = 'absolute';
document.querySelector('.textbar.style_2.wpb_content_element').style.marginBottom = '150px';

//lets rewrite this form without the labels
let newForm = `
<form action="/engineer-application-sandbox-v1/#wpcf7-f949-p950-o1" method="post"
class="wpcf7-form eng-sandbox-form init" novalidate="novalidate" data-status="init">
<div style="display: none">
  <input type="hidden" name="_wpcf7" value="949" />
  <input type="hidden" name="_wpcf7_version" value="5.5.3" />
  <input type="hidden" name="_wpcf7_locale" value="en_US" />
  <input type="hidden" name="_wpcf7_unit_tag" value="wpcf7-f949-p950-o1" />
  <input type="hidden" name="_wpcf7_container_post" value="950" />
  <input type="hidden" name="_wpcf7_posted_data_hash" value="" />
</div>
<p>
  <label>
    <span class="wpcf7-form-control-wrap your-name"><input placeholder="first and last name*" type="text" name="your-name" value="" size="40"
        class="wpcf7-form-control wpcf7-text" aria-invalid="false" /></span></label><br />
  <label>
    <span class="wpcf7-form-control-wrap YourEmail"><input placeholder="email address*" type="email" name="YourEmail" value="" size="40" class="
          wpcf7-form-control
          wpcf7-text
          wpcf7-email
          wpcf7-validates-as-required
          wpcf7-validates-as-email
        " aria-required="true" aria-invalid="false" /></span></label><br />
  <label>
    <span class="wpcf7-form-control-wrap your-message">
      <textarea placeholder="your message*" name="your-message" cols="40" rows="10" class="wpcf7-form-control wpcf7-textarea"
        aria-invalid="false"></textarea></span></label><br />
  <input type="submit" value="Send" class="wpcf7-form-control has-spinner wpcf7-submit" /><span
    class="wpcf7-spinner"></span>
</p>
<p style="display: none !important">
  <label>Δ<textarea name="_wpcf7_ak_hp_textarea" cols="45" rows="8" maxlength="100"></textarea></label><input
    type="hidden" id="ak_js" name="_wpcf7_ak_js" value="1639792666119" />
  <script>
    document
      .getElementById("ak_js")
      .setAttribute("value", new Date().getTime());
  </script>
</p>
<div class="wpcf7-response-output" aria-hidden="true"></div>
</form>
`;

//Inject new form into DOM
document.querySelector('form.wpcf7-form.eng-sandbox-form.init').innerHTML = newForm;

//style the submit button
document.querySelector('input.wpcf7-form-control.has-spinner.wpcf7-submit').style.width = '50%';
document.querySelector('input.wpcf7-form-control.has-spinner.wpcf7-submit').style.float = 'right';
document.querySelector('input.wpcf7-form-control.has-spinner.wpcf7-submit').style.marginRight = '25px';

/* END Of Form Restyling Code */

Exercise 3: Cookie monster
Hypothesis: Disallowing return users to resubmit the email form will decrease spam.

Device: Desktop only

URL: https://surefoot.me/engineer-application-sandbox-v1/

Dev Notes:
To start, I am setting up some code that will "listen" for a form submittal. When that event occurs, I am checking to see if the email that was entered has been previously entered. If not, add that users email to my "database" and continue on with form submission. If it has been enetered previously, then I'm replacing the form with a Jim GIF that is sure to improve our conversion rate.

If user has already submitted the email form, don’t allow them to resubmit. Instead, show the message "Hmm, you look familiar. While you're waiting for our reply, here's a GIF we think you should see."
GIF can be anything you desire.
Styling of messaging is up to you.
Include a few lines of a README-esque description that explains your code to a non-technical person.
Your code here:

/* Cookie Monster Code */

//get references to form and email 
let form = document.querySelector('form.wpcf7-form.eng-sandbox-form.init');
let email = document.querySelector('input.wpcf7-form-control.wpcf7-text.wpcf7-email.wpcf7-validates-as-required.wpcf7-validates-as-email');

//initialize variable with empty array that will act as my database
let usersEmail = [];
//add Sumbit event listener to form
form.addEventListener('submit', () => {
    //check if the value of email field exists in my array, if not add email to array
    if(usersEmail.indexOf(email.value) === -1) {
        usersEmail.push(email.value);
    } else {
        //Otherwise, the email must have already been used, so replace form HTML with message plus awesome Office GIF.
        form.innerHTML = `<h4>Hmm, you look familiar. While you're waiting for our reply, here's a GIF we think you should see.</h4><div style="width:100%;height:0;padding-bottom:83%;position:relative;"><iframe src="https://giphy.com/embed/Yycc82XEuWDaLLi2GV" width="100%" height="100%" style="position:absolute" frameBorder="0" class="giphy-embed" allowFullScreen></iframe></div><p><a href="https://giphy.com/gifs/theoffice-the-office-episode-24-tv-Yycc82XEuWDaLLi2GV">via GIPHY</a></p>`;
        
    }
});

/* End Of Cookie Monster Code */
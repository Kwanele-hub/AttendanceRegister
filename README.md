# AttendanceRegister

 This is an AttendanceRegister that will use responsive bootstrap ui form to capture student attendance for TCG.
 Where a student should be able to enter their Name, Surname, Phone Number, Email Address and Date.

 Step 01: Create a new Google Sheet on your Google Drive
Create a new Google Sheet and add column labels as shown in the below image (these column names are not used in the programme, it is only to identify the data stored underneath)

Step 02. Creating the HTML form
Open the script editor from Tools → Script editor in your Google Sheet.

Then, replace code in the Code.gs file with the following code.

function doGet(request) {
  return HtmlService.createTemplateFromFile('Index').evaluate();
}

Step 03. Sending Form Data to Google Sheet
Using google.script.run asynchronous client-side JavaScript API, we can call server-side Apps Script functions from HTML-service pages.

The following JavaScript, calls the server-side function processForm once you click the submit button. To add this JavaScript, create a new HTML file and name it ass JavaScript. Then replace the auto-generated code with the following.

<script>
  
  function preventFormSubmit() {
    var forms = document.querySelectorAll('form');
    for (var i = 0; i < forms.length; i++) {
      forms[i].addEventListener('submit', function(event) {
      event.preventDefault();
      });
    }
  }
  window.addEventListener('load', preventFormSubmit);    
      
      
  function handleFormSubmit(formObject) {
    google.script.run.processForm(formObject);
    document.getElementById("myForm").reset();
  }
</script>

Step 04. Deploying a script as a web app
Now you can deploy the above code as a web app by going to Publish → Deploy as a web app… Then select New for the project version and click update. Copy the Current web app URL in the next dialog box and click OK. Paste the copied URL in the browser to get the form. You can read more about Deploying a script as a web app from this Google Apps Script Guide.


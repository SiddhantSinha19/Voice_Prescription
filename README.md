VOICE PRESCRIPTION APPLICATION

OVERVIEW
This is web application for hospitals to make the process of medical prescription simple and digitized. In the model the doctor will record the prescription as voice and the model will convert speech to text using Speech Recognition library in python. Then this prescription will be displayed on the doctors screen. He can edit the same manually. This voice input will further be used for extraction of name, age , gender, symptoms, diagnosis, vaccines, medication and advise. The final pdf is generated by structuring the extracted info and is made available in Hindi, English and Kannada. This can be mailed/WhatApp to the recepients address.

The audio is recorded using record.js javascript library 
https://cdn.rawgit.com/mattdiamond/Recorderjs/08e7abd9/dist/recorder.js

Speech to text conversion was done using google translator via a python library - speech_recognition

r = sr.Recognizer()

path_my = "/Users/siddhantsinha19/Downloads/"+filename

AUDIO_FILE = path.join(path.dirname(path.realpath(__file__)), path_my)

with sr.AudioFile(AUDIO_FILE) as source:     # mention source it will be either Microphone or audio files.

  audio = r.record(source)
  
  try:
  
    text = r.recognize_google(audio)    # use recognizer to convert our audio into text part.
                
  except:
  
    text="Sorry could not recognize your voice" 

The above code converts audio and stores it a variable text

After the text is stored.
Various functions extract required details from the entire text corpus

-extractPatientDetails() - extracts name, age and sex of the patient

-extract_symps() - extracts the symptoms complained by the patient

-get_disease() - extract the disease/diagnosis said by the doctor 

-extract_medicines() - extracts the prescription given

-extract_advice() - extracts advice given by the doctor

After the extration process is completed, each of them is sent to a <textarea> tag in html and doctor and edit anything over there
  
Once the doctor is satisfied, he can click on "generate pdf" button and get the english and hindi pdf.
Pdf is created using the python library fpdf. Implementation can be found in the functions - createPDF() - for english pdf and pdf_hin_kan() for hindi pdf. English to Hindi conversion is done using google transalator.

The pdf can be viewed, emailed or sent on whatsapp.
The implentation of whatsapp is done using twilio. API key needs to be created and the whatsapp can only be sent on registered number using unpaid version.
The implementation of email is straightforward and is done using a python library called email. It's implementation can be found in the function sendEmailfun().

Further the front end is created using HTML,CSS, and Javascript. And for the backend we have used flask.

For any queries, please contact - Shivangi Shukla - shivangishukla167@gmail.com or 
Siddhant Sinha - sid.ronaldo1904@gmail.com
Also, please mention the github link/ cite the source if you are using any of our work.

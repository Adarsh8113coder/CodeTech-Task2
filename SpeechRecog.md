import speech_recognition as sr
recognizer = sr.Recognizer()
recognizer.energy_threshold = 300
recognizer.dynamic_energy_threshold = True
with sr.Microphone() as source:
    print(" Adjusting microphone for noise")
    print(" Please wait for 3 seconds")
    recognizer.adjust_for_ambient_noise(source, duration=3)
    print("Microphone adjusted successfully\n")
    print(" Speak something...")
    audio = recognizer.listen(source)
    print("Processing speech...\n")
try:
    text = recognizer.recognize_google(audio)
    print(" TRANSCRIBED TEXT ")
    print(text)

except sr.UnknownValueError:

    print("Could not understand audio")

except sr.RequestError:

    print("Internet connection error")

except Exception as e:

    print("Error:", e)

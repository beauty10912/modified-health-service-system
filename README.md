# modified-health-service-system
class HealthSystem:
    def __init__(self):
        self.patients = {}
        self.appointments = {}
        # Expanded knowledge base of sicknesses with symptoms and remedies
        self.sickness_knowledge_base = [
            {"sickness": "Flu", "symptoms": ["fever", "cough", "sore throat"], "remedy": "Rest, hydrate, and take over-the-counter flu medicine."},
            {"sickness": "Cold", "symptoms": ["runny nose", "sore throat", "cough"], "remedy": "Rest, drink warm liquids, and use a nasal decongestant."},
            {"sickness": "Migraine", "symptoms": ["headache", "nausea", "sensitivity to light"], "remedy": "Rest in a dark room, stay hydrated, and use over-the-counter painkillers."},
            {"sickness": "Allergy", "symptoms": ["sneezing", "itchy eyes", "runny nose"], "remedy": "Avoid allergens, take antihistamines, and stay indoors when pollen count is high."},
            {"sickness": "Gastroenteritis", "symptoms": ["nausea", "vomiting", "diarrhea"], "remedy": "Stay hydrated with electrolyte solutions and eat light meals until symptoms improve."},
            {"sickness": "Tension Headache", "symptoms": ["headache", "tight neck muscles"], "remedy": "Relax, stretch the neck, and take over-the-counter pain relievers."},
            {"sickness": "Asthma", "symptoms": ["shortness of breath", "wheezing", "coughing"], "remedy": "Use an inhaler, avoid triggers, and monitor symptoms."},
            {"sickness": "Pneumonia", "symptoms": ["cough", "fever", "difficulty breathing"], "remedy": "Antibiotics (if bacterial), rest, and plenty of fluids."},
            {"sickness": "Diabetes", "symptoms": ["increased thirst", "frequent urination", "fatigue"], "remedy": "Manage blood sugar with diet, exercise, and medication."},
            {"sickness": "Hypertension", "symptoms": ["headaches", "shortness of breath", "nosebleeds"], "remedy": "Blood pressure medication, reduce salt intake, exercise regularly."},
            {"sickness": "Anemia", "symptoms": ["fatigue", "pale skin", "shortness of breath"], "remedy": "Iron supplements, eat iron-rich foods."},
            {"sickness": "Depression", "symptoms": ["persistent sadness", "fatigue", "loss of interest"], "remedy": "Counseling, medication, lifestyle changes."},
            {"sickness": "Arthritis", "symptoms": ["joint pain", "swelling", "stiffness"], "remedy": "Anti-inflammatory medications, exercise, physical therapy."},
            {"sickness": "Chickenpox", "symptoms": ["itchy rash", "fever", "fatigue"], "remedy": "Antihistamines for itching, rest, and fever reducers."},
            {"sickness": "Sinusitis", "symptoms": ["nasal congestion", "headache", "facial pain"], "remedy": "Nasal decongestants, warm compresses, hydration."},
            {"sickness": "Stomach Ulcer", "symptoms": ["burning stomach pain", "nausea", "vomiting"], "remedy": "Avoid spicy foods, take antacids, and follow a bland diet."},
            {"sickness": "Tuberculosis", "symptoms": ["persistent cough", "fever", "weight loss"], "remedy": "Antibiotics (long-term), rest, and avoid contact with others."},
            {"sickness": "Hepatitis", "symptoms": ["fatigue", "nausea", "yellowing of skin"], "remedy": "Antiviral drugs, avoid alcohol, rest, and maintain a healthy diet."},
            {"sickness": "Shingles", "symptoms": ["painful rash", "blisters", "fever"], "remedy": "Antiviral medications, pain relievers, and keeping the rash clean."},
            {"sickness": "Laryngitis", "symptoms": ["hoarseness", "sore throat", "loss of voice"], "remedy": "Rest your voice, drink warm liquids, and avoid irritants."},
            {"sickness": "Cystitis", "symptoms": ["frequent urination", "painful urination", "bloody urine"], "remedy": "Antibiotics, drink plenty of water, avoid irritants like caffeine."},
            {"sickness": "Urinary Tract Infection (UTI)", "symptoms": ["painful urination", "frequent urination", "cloudy urine"], "remedy": "Antibiotics, increase water intake, and take pain relievers."},
            {"sickness": "Dengue Fever", "symptoms": ["high fever", "joint pain", "rash"], "remedy": "Rest, hydrate, and take acetaminophen for fever."},
            {"sickness": "Malaria", "symptoms": ["fever", "chills", "sweating"], "remedy": "Antimalarial medications, rest, and hydration."},
            {"sickness": "Gout", "symptoms": ["severe joint pain", "redness", "swelling"], "remedy": "Take anti-inflammatory medications, elevate the affected joint, and drink plenty of water."},
            {"sickness": "Heartburn", "symptoms": ["burning sensation in chest", "regurgitation", "sore throat"], "remedy": "Antacids, eat smaller meals, avoid lying down after eating."},
            {"sickness": "Sleep Apnea", "symptoms": ["snoring", "difficulty sleeping", "daytime fatigue"], "remedy": "Use a CPAP machine, avoid alcohol, maintain a healthy weight."},
            {"sickness": "Celiac Disease", "symptoms": ["bloating", "diarrhea", "fatigue"], "remedy": "Follow a strict gluten-free diet."},
            {"sickness": "Influenza B", "symptoms": ["fever", "cough", "muscle aches"], "remedy": "Rest, hydrate, and take antiviral medications if prescribed."},
            {"sickness": "Chronic Fatigue Syndrome", "symptoms": ["extreme tiredness", "sore throat", "muscle pain"], "remedy": "Rest, pacing activities, and a healthy diet."},
            {"sickness": "Psoriasis", "symptoms": ["red patches of skin", "scaly skin", "itching"], "remedy": "Topical treatments, UV light therapy, and avoiding triggers."},
            {"sickness": "Gallstones", "symptoms": ["abdominal pain", "nausea", "indigestion"], "remedy": "Surgical removal of gallstones, medication to dissolve stones."},
            {"sickness": "Appendicitis", "symptoms": ["abdominal pain", "fever", "nausea"], "remedy": "Surgical removal of the appendix, antibiotics."},
            {"sickness": "Panic Attack", "symptoms": ["rapid heartbeat", "sweating", "shortness of breath"], "remedy": "Breathing exercises, relaxation techniques, and therapy."},
            {"sickness": "Conjunctivitis (Pink Eye)", "symptoms": ["red eyes", "itchy eyes", "tearing"], "remedy": "Antihistamines, eye drops, and avoid touching the eyes."},
            {"sickness": "Chronic Bronchitis", "symptoms": ["cough", "mucus production", "shortness of breath"], "remedy": "Avoid smoking, inhalers, and bronchodilators."},
            {"sickness": "Sickle Cell Anemia", "symptoms": ["painful episodes", "fatigue", "swelling of hands and feet"], "remedy": "Pain management, blood transfusions, and hydration."},
            {"sickness": "Eczema", "symptoms": ["itchy, dry skin", "red patches", "swelling"], "remedy": "Topical steroids, moisturizers, and avoiding triggers."},
            {"sickness": "Tonsillitis", "symptoms": ["sore throat", "fever", "swollen tonsils"], "remedy": "Rest, warm saltwater gargles, and antibiotics if bacterial."},
            {"sickness": "Leukemia", "symptoms": ["fatigue", "easy bruising", "fever"], "remedy": "Chemotherapy, radiation therapy, and bone marrow transplant."},
            {"sickness": "Thyroid Disorders", "symptoms": ["fatigue", "weight changes", "mood swings"], "remedy": "Thyroid hormone replacement or medication."},
            {"sickness": "Cystic Fibrosis", "symptoms": ["persistent cough", "difficulty breathing", "lung infections"], "remedy": "Antibiotics, mucus thinning agents, and physical therapy."},
            {"sickness": "Osteoporosis", "symptoms": ["bone fractures", "back pain", "loss of height"], "remedy": "Calcium and vitamin D supplements, weight-bearing exercises."}
        ]

    def sickness_input(self):
        sickness_name = input("Enter the name of the sickness: ").capitalize()
        
        # Check if the sickness is in the knowledge base
        sickness_found = None
        for sickness in self.sickness_knowledge_base:
            if sickness["sickness"].lower() == sickness_name.lower():
                sickness_found = sickness
                break
        
        if sickness_found:
            symptoms = ", ".join(sickness_found["symptoms"])
            remedy = sickness_found["remedy"]
            print(f"\nSickness: {sickness_name}")
            print(f"Symptoms: {symptoms}")
            print(f"Suggested Remedy: {remedy}")
        else:
            print("Sickness not found in the system. Please consult a healthcare professional.")

# Main Loop to interact with the system
def main():
    system = HealthSystem()

    while True:
        print("\nHealth Service System")
        print("1. Add Patient")
        print("2. Schedule Appointment")
        print("3. Cancel Appointment")
        print("4. Reschedule Appointment")
        print("5. Input Sickness and Get Remedies")
        print("6. View Patient Details")
        print("7. View Patient Notifications")
        print("8. View All Appointments")
        print("9. Exit")

        choice = input("Enter your choice: ")

        if choice == '1':
            system.add_patient()
        elif choice == '2':
            system.schedule_appointment()
        elif choice == '3':
            system.cancel_appointment()
        elif choice == '4':
            system.reschedule_appointment()
        elif choice == '5':
            system.sickness_input()  # Let the user input the sickness and get the remedy
        elif choice == '6':
            system.view_patient_details()
        elif choice == '7':
            system.view_patient_notifications()
        elif choice == '8':
            system.view_all_appointments()
        elif choice == '9':
            print("Exiting system...")
            break
        else:
            print("Invalid choice, please try again.")

# Run the system
if __name__ == "__main__":
    main()


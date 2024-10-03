import random
hair_colors = ['Black', 'Brown', 'Blonde']
ear_lobe_attachments = ['Attached', 'Detached']
eye_colors = ['Brown', 'Blue', 'Green']
genders = ['Male', 'Female']
mutation_status = ['Yes', 'No']
male_names = ["Aravind", "Bhavesh", "Chirag", "Devang", "Eshan", "Gaurav", "Harish", "Ishwar", "Jaideep", "Kaushik", 
              "Lakshya", "Manish", "Nikhil", "Omkar", "Prashant", "Rahul", "Sahil", "Tushar", "Uday", "Varun", 
              "Yash", "Zahir", "Abhinav", "Chaitanya", "Divyansh"]

female_names = ["Aanya", "Aisha", "Aditi", "Alia", "Ananya", "Anushka", "Aradhya", "Arika", "Avni", "Bhumika", 
                "Chaitra", "Diya", "Eesha", "Garima", "Harsha", "Ishita", "Janhavi", "Kavya", "Lakshmi", "Mahima", 
                "Nandini", "Priya", "Rashi", "Saanvi", "Tanvi", "Uma", "Vaishnavi", "Yashaswini", "Zoya"]

def generate_unique_names(num_names, name_list):
    if num_names > len(name_list):
        raise ValueError("Not enough unique names available")
    return random.sample(name_list, num_names)

def generate_individuals(num_individuals):
    num_males = num_individuals // 2
    num_females = num_individuals - num_males 
    males = generate_unique_names(num_males, male_names)
    females = generate_unique_names(num_females, female_names)
    individuals = []
    for name in males:
        individual = {
            'Name': name,
            'Gender': 'Male',
            'Hair Color': random.choice(hair_colors),
            'Ear Lobe Attachment': random.choice(ear_lobe_attachments),
            'Height': round(random.uniform(150, 200), 2),
            'Eye Color': random.choice(eye_colors),
            'Mutation': random.choice(mutation_status) 
        }
        individuals.append(individual)
    
    for name in females:
        individual = {
            'Name': name,
            'Gender': 'Female',
            'Hair Color': random.choice(hair_colors),
            'Ear Lobe Attachment': random.choice(ear_lobe_attachments),
            'Height': round(random.uniform(150, 200), 2), 
            'Eye Color': random.choice(eye_colors),
            'Mutation': random.choice(mutation_status)
        }
        individuals.append(individual)
    
    random.shuffle(individuals) 
    return individuals

def calculate_suitability_score(individual):
    if individual['Mutation'] == 'Yes':
        return -float('inf') 
    
    score = 0
    
    if individual['Hair Color'] == 'Black':
        score += 3
    elif individual['Hair Color'] == 'Brown':
        score += 2
    elif individual['Hair Color'] == 'Blonde':
        score += 1
    
    if individual['Ear Lobe Attachment'] == 'Attached':
        score += 2
    elif individual['Ear Lobe Attachment'] == 'Detached':
        score += 1
    
    score += individual['Height'] / 10 
    
    if individual['Eye Color'] == 'Brown':
        score += 3
    elif individual['Eye Color'] == 'Blue':
        score += 2
    elif individual['Eye Color'] == 'Green':
        score += 1
    
    return score

def select_top_individuals(individuals, top_n):
    eligible_individuals = [individual for individual in individuals if individual['Mutation'] == 'No']
    
    scored_individuals = [(individual, calculate_suitability_score(individual)) for individual in eligible_individuals]
    scored_individuals.sort(key=lambda x: x[1], reverse=True) 
    
    return scored_individuals[:top_n]

num_individuals = 50
top_n = 10


individuals = generate_individuals(num_individuals)

print("List of 50 Individuals:")
for i, individual in enumerate(individuals, 1):
    print(f"Individual {i}: {individual}")

top_individuals = select_top_individuals(individuals, top_n)

print("\nTop 10 Individuals by Suitability Score:")
for i, (individual, score) in enumerate(top_individuals, 1):
    print(f"{i}. {individual['Name']}")

# programa-asistido-en-java
DESARROLLAR UN PROGRAMA DE “INSTRUCCIÓN ASISTIDA POR COMPUTADORA” EN LENGUAJE JAVA"
import random

class CAI:
    def __init__(self):
        self.score = 0
        self.total_questions = 0
        self.difficulty = 1
        self.operation = 1

    def generate_question(self):
        num1 = random.randint(1, 10**self.difficulty)
        num2 = random.randint(1, 10**self.difficulty)
        if self.operation == 1:
            question = f"What is {num1} + {num2}? "
            answer = num1 + num2
        elif self.operation == 2:
            question = f"What is {num1} - {num2}? "
            answer = num1 - num2
        elif self.operation == 3:
            question = f"What is {num1} * {num2}? "
            answer = num1 * num2
        elif self.operation == 4:
            question = f"What is {num1} / {num2}? "
            answer = num1 / num2

        return question, answer

    def start(self):
        while self.total_questions < 10:
            question, answer = self.generate_question()
            user_answer = int(input(question))

            if user_answer == answer:
                feedback = random.choice(["¡Muy bien!", "¡Excelente!", "¡Buen trabajo!", "¡Sigue así!"])
                print(feedback)
                self.score += 1
            else:
                feedback = random.choice(["No. Por favor intenta de nuevo.", "Incorrecto. Intenta una vez más.", "¡No te rindas!", "No. Sigue intentando."])
                print(feedback)

            self.total_questions += 1

        accuracy = (self.score / self.total_questions) * 100
        if accuracy < 75:
            print("Por favor pide ayuda adicional a tu instructor")
        else:
            print("Felicidades, estás listo para pasar al siguiente nivel!")

if __name__ == "__main__":
    cai = CAI()
    cai.difficulty = int(input("Elige el nivel de dificultad (1, 2, etc.): "))
    cai.operation = int(input("Elige el tipo de problema aritmético (1: suma, 2: resta, 3: multiplicación, 4: división): "))
    cai.start()

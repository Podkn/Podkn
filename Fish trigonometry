import random
import sympy as sp
good=0
bad=0

x = sp.symbols('x')
functions = {
    "sin": sp.sin,
    "cos": sp.cos,
    "tan": sp.tan,
    "ctg": lambda x: 1 / sp.tan(x)
}


#angle_deg = [0, 30, 45, 60, 90]
angle_deg = [0, 30, 45, 60, 90, 120, 135, 150, 180, 210, 225, 240, 270, 300, 315, 330, 360]
angle_rad = [sp.rad(angle) for angle in angle_deg]


angle_map = dict(zip(angle_deg, angle_rad))


def parse_answer(answer):
    parsed_answer = answer.replace('sqrt', 'p').replace('(','').replace(')','').replace('zoo','')
    #print(answer,parsed_answer)
    return parsed_answer

def ask_question():
    global good
    global bad
    func_name, func = random.choice(list(functions.items()))  # Losowanie funkcji (sin, cos)
    angle = random.choice(angle_deg)  # Losowanie kąta

    print(f"Ile wynosi {func_name}({angle}°)?")

     #user_answer = str(input("Odpowiedź (używaj p jako sqrt, np. -p3/2): "))
    user_answer = str(input("Odpowiedź: "))
    try:

        correct_value = sp.simplify(func(angle_map[angle]))
        correct_value = parse_answer(str(correct_value))

        if user_answer==correct_value:
            print("Dobrze!")
            good+=1
        else:

            print(f"\033[91mŹle! Poprawna odpowiedź to: {correct_value}\033[0m")

            bad+=1
    except sp.SympifyError:
        print("Błąd: Niepoprawne wyrażenie! Spróbuj ponownie.")
    print( good," ",bad)

def start_quiz():
    #print("Rozpoczynamy quiz trygonometryczny! Odpowiedzi w postaci symbolicznej (np. -p3/2).")
    while True:
        ask_question()
        #again = input("Chcesz kontynuować? (tak/nie): ").lower()
        again="tak"
        if again != "tak":
            print("Dzięki za udział w quizie!")
            break


start_quiz()

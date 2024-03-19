# Yashfeen_SafaAkhtar_BMI_Calculator
The repo is build during the class i taught during march 2024 when we were to make streamlit application using chatGPT
import streamlit as st
import numpy as np

def quadratic_roots(a, b, c):
    # Calculate discriminant
    discriminant = b**2 - 4*a*c
    
    # Check if discriminant is positive, negative, or zero
    if discriminant > 0:
        # Two real and distinct roots
        root1 = (-b + np.sqrt(discriminant)) / (2*a)
        root2 = (-b - np.sqrt(discriminant)) / (2*a)
        return root1, root2
    elif discriminant == 0:
        # Two real and equal roots
        root = -b / (2*a)
        return root, root
    else:
        # Complex roots
        real_part = -b / (2*a)
        imaginary_part = np.sqrt(abs(discriminant)) / (2*a)
        root1 = complex(real_part, imaginary_part)
        root2 = complex(real_part, -imaginary_part)
        return root1, root2

# Streamlit application
def main():
    st.title("Quadratic Equation Solver")
    st.write("This app calculates the roots of a quadratic equation ax^2 + bx + c = 0 and checks if they are even or odd.")

    # Input coefficients
    a = st.number_input("Enter coefficient a", value=1.0)
    b = st.number_input("Enter coefficient b", value=0.0)
    c = st.number_input("Enter coefficient c", value=0.0)

    # Calculate roots
    if st.button("Calculate Roots"):
        root1, root2 = quadratic_roots(a, b, c)
        st.success(f"Root 1: {root1}")
        st.success(f"Root 2: {root2}")

        # Check if roots are even or odd
        root1_type = "Even" if root1 % 2 == 0 else "Odd"
        root2_type = "Even" if root2 % 2 == 0 else "Odd"
        st.info(f"Root 1 is {root1_type}")
        st.info(f"Root 2 is {root2_type}")

if __name__ == "__main__":
    main()

import re  #regular expression
import streamlit as st

#page styling

st.set_page_config(page_title= "Passwords Strenght Meter",page_icon="🔑",layout="centered")

#custom css
st.markdown("""
<style>
.main {text.align: center;}
.stTextInput {width: 60% !important; margin: auto}
.stButton button {width: 50%; background-color: #4CAF50; color: white; font-size: 18px;} 
.stButton button:hover {background-color:rgb(18, 238, 29); color:black;}
</style>
""", unsafe_allow_html=True)

#page title & description
st.title("passwords_strength_meter 🔒")
st.write("Enter your password below to check its security level 🛡️")

#function to check strength
def check_password_strength(password):
    score = 0
    feedback = []

#conditions for scoring
    if len(password) >= 8:
        score += 1    #increased score by 1

    else:
        feedback.append("❌ password shuold be **at least 8 characters long**.") 

    if re.search(r"[A-Z]", password) and re.search(r"[a-z]", password): 
        score += 1
    else:
        feedback.append("❌ password shuold include **both uppercase(A-Z) and lowercase(a-z)**.")

    if re.search(r"\d", password):
        score += 1

    else:
        feedback.append("❌ password shuold include **at least one number (0-9)**.")

    #special characters
    if re.search(r"[!@#$%^&*]", password):
      score += 1

    else:
        feedback.append("❌ Include **at least one special character (!@#$%^&*)**.")   

    #display result
    if score == 4:
        st.success("✔️ **Strong password** - your password is secure.")

    elif score == 3:
      st.info("⚠️ **Moderate password** - your password is moderately secure.") 

    else:
        st.error("❌ **Weak password** _follow the suggestion below to improve it.")

    #feedback
    if feedback:
        with st.expander("🌘 **Improve your password** "):
            for item in feedback:
                st.write(item)

password = st.text_input("Enter your password 🔑", type="password", help="Ensure your password is strong and seccure 🔐")

#button working
if st.button("Check Strength"):
    if password:
        check_password_strength(password)

    else:
        st.warning("⚠️ Please enter a password first!")  #show waring if password is empty~  


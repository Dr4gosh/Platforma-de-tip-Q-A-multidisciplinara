# Platforma-de-tip-Q-A-multidisciplinara
Proiect Licenta
def login_verify(event):
    global directory
    global A
    global N
    N = StringVar()
    A = 0
    username1 = username_verify.get()
    password1 = password_verify.get()
    user_path = 'Users/' + username1
    try:
        file1 = open(user_path, "r")
        verify = file1.read().splitlines()
        N = verify[2]
        if "Admin" in verify:
            A = 1
        if password1 in verify:
            login_sucess()
            screen2.unbind("<Return>")
        else:
            password_not_recognised()
            password_entry1.delete(0, END)
    except FileNotFoundError:
        user_not_found()
        username_entry1.delete(0, END)
        password_entry1.delete(0, END)
    except PermissionError:
        error6()



class Registration_form:# Registration_form degan class ochildi
    royxat  = {"Ali|Vali":'1234'}# royxat listi ochildi
    def __init__(self) -> None: # ishga tushuradi
        pass #hich narsa qaytarmaydi


    ####################################
    ########## CLASSMETHODLAR ##########
    ####################################
    @classmethod
    def check_pwd(self, p1, p2):#check_pwd degan funksiya ochildi va p1 va p2lar soraladi
        if p1 == p2:# agar p1 p2ga teng bolsa
            return True#qaytarib beradi togri qiymat
        else:# aks holda
            return False# qaytarib beradi yolgon qiymat

    
    @classmethod
    def view(self, usr, id):# view degan degan funksiya ochildidegan def ochildi va usr idlar soraladi
        if id == Registration_form.royxat[usr]['id']:#agar id teng bolsa Registration_formning  royxat usr va id bolsa
            print(f"Sizning parolingiz {(Registration_form.royxat[usr]['password'])}")#ekranga chiqarib beradi
        else:# aks holda
            print('Siz ushbu shaxs ekanligingizga shubxa bor')#ekranga chiqarib bradi


    @classmethod
    def msid(self):#msid degan funksiya ochildi
        import random#random modulini chaqirib oldi
        uid = ''#uid degan str ochdi
        for i in range(6):#1 dan  6 gacha sonlarni oladi
            uid += str(random.randint(0, 9))#uid qoshib ket 
        return uid#qaytarib ber uid

    
    
    ####################################
    ############ METHODLAR #############
    ####################################
    def register(self, name, surname, pwd, pwd_again):# registerdegan funksiya ochildi name, surname, pwd, pwd_again malumotlarni soraydi
        self.name = name# class ga tegishli funsiya bolganligi uchun self ga tengladik
        self.surname = surname# class ga tegishli funsiya bolganligi uchun self ga tengladik
        self.pwd = pwd# class ga tegishli funsiya bolganligi uchun self ga tengladik
        self.pwd_again = pwd_again# class ga tegishli funsiya bolganligi uchun self ga tengladik
        self.tekshiruv = Registration_form.check_pwd(self.pwd, self.pwd_again)# tekshiruvdegan yangi ozgaruvchi olindi va unga check_pwd metodini chaqirdik
        self.full = f'{self.name}|{self.surname}'#full degan yangi ozgaruvchi yaratdik unga name va surname ni tengladi
        self.activate = Registration_form.msid()#activate degan ozgaruvchi ochildi va Registration_formga msid funksiyasini chaqirdi
        
        self.ijro = {'password':self.pwd,
        'id':self.activate}# ijro degan yangi ozgaruvchi ochildi va unga lugat ichida password:pwd va id : activate tengladi
        if self.tekshiruv and self.full not in list((Registration_form.royxat).keys()):#agar tekshiruv va full list ning Registration_formning royxat bolinganda ichida bolmasa 
            Registration_form.royxat[self.full] = self.ijro#Registration_formning ichida royxatning full ning ichidagi element teng bolsa ijroga
            print("Siz muvaffaqiyatli ro`yxatdan o`tdingiz")#chop etadi Siz muvaffaqiyatli ro`yxatdan o`tdingiz
            print(f'Sining aktivatsiya kodinggiz {self.activate}')#chop etadi Sining aktivatsiya kodinggiz deb activateni malumotini chiqarib beradi
        elif self.tekshiruv == False:#aks holda tekshiruv teng bolsa yolgon qiymat qaytaradi
            print("Kiritgan parollaringiz bir biriga mos kelmadi")#chop etadi Kiritgan parollaringiz bir biriga mos kelmadi
        elif self.full in list((Registration_form.royxat).keys()):#aks holda fullni ichida Registration_formning royxatni bolganda 
            print('Siz oldin ro`yxatdan o`tgansiz')#chop et Siz oldin ro`yxatdan o`tgansiz
            
        else:# aks holda 
            print("Kutilmagan hatolik ro`y berdi")#chop etib ber Kutilmagan hatolik ro`y berdi

    
    

    def signin(self, username, passwd):# signing funksiyasi ochilda va unga username, passwd argument ni berdi
        self.username = username#classga tegishli bolgani uchun self qoydik
        self.passwd = passwd#classga tegishli bolgani uchun self qoydik
        if self.username in list((Registration_form.royxat).keys()):#agar usernameni ichida Registration_formni ichida royxat bolganda
            if self.passwd == Registration_form.royxat[username]['password']:#agar passwd teng bolganda Registration_formni ichida royxatga username va password
                print('Ishchi oynaga xush kelibsiz')#chop et Ishchi oynaga xush kelibsiz
            else:#aks holda 
                javob = input('Agar parolingiz esdan chiqqan bo`lsa, uni tiklash uchun 1 ni kiriting: ')#javob degan soraydigan ozgaruvchi olinib Agar parolingiz esdan chiqqan bo`lsa, uni tiklash uchun 1 ni kiriting:ni soraydi 
                if javob == '1':#agar javob teng bolsa 1ga 
                    id = input('Aktivatsiya kodini kiriting: ')#id degan soraydigan ozgaruvchi olib Aktivatsiya kodini kiriting: ni soraydi
                    Registration_form.view(self.username, id)#Registration_formni ichida view funksiyasi chaqirib username, id ni berdik

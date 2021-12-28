import random
import time # geri sayım için kullanıldı

def saldiri_buyuklugu():
    while True:
        deger = int(input("Saldırı büyüklüğünüzü 1 ile 50 arasında seçin: "))

        if deger > 50:
            print ("Saldırı büyüklüğü 1 ile 50 arasında olmalıdır.")
        elif deger < 1:
            print ("Saldırı büyüklüğü 1 ile 50 arasında olmalıdır.")
        else:
            return deger

def attack(can, isim):

    M_sansi = random.randint(0, 70) # *** 50 yapınca büyük saldırılar çok zorlaşıyor ***
    print ("\n---------------", isim, "Saldırı !! ---------------")
    M_saldirisi = saldiri_buyuklugu() 

    if M_sansi > M_saldirisi: # ne kadar küçük saldırırsan o kadar çok şansınız olur.
        print ("\n", isim, M_saldirisi, "hasar", "verdi!!\n")
        can -= M_saldirisi
    else:
        print ("\nOoopsy!", isim, "saldırıyı kaçırdı!")

    return can

def hpstatus(can1, can2, usr1, usr2):
    sopa1 = int(can1/2)
    sopa2 = int(can2/2)
    print("", usr1, "\n", "HP [%s]:" % can2, "|" * sopa1, "\n", usr2, "\n", "HP [%s]:" % can1, "|" * sopa2) # f string yerine %s komutunu öğrendim, onu kullandım.

def username(siralama, kahramanlarin_ismi):
    while True:
        print ('-----', siralama, 'Kahraman -----')

        isim = str(input("Lütfen kahramanınızın adını yazın: "))
        isim = isim.capitalize()

        if len(isim) <= 1:
            print ("Kahramının ismi tek karakterden uzun olmalıdır.")        
        elif isim in kahramanlarin_ismi:
            print (isim, "alındı, lütfen başka isim seçin!")
        else:
            break

    return isim

def main():

    oyuncular = []

    kahraman_adi = username("İlk", oyuncular)
    oyuncular.append(kahraman_adi)

    kahraman_adi = username("İkinci", oyuncular)
    oyuncular.append(kahraman_adi)

    random.shuffle(oyuncular)

    kazanan  = oyuncular[0]
    kaybeden = oyuncular[1] 

    print ("\nYazı tura sonucu: %s önce başlar!" % kazanan) # *** Yazı tura sonucu *** 
    print ("\nOyun 3 saniye içinde başlıyor!") # *** geri sayım  ***
    time.sleep(1)
    print ("---2---")
    time.sleep(1)
    print ("---1---")
    time.sleep(1)
    print ("\n"*1)

    durum = True

    while durum:

        # *** rövanş canları ***
        can1, can2 = (100, 100)
        hpstatus(can1, can2, kazanan, kaybeden)

        # *** oyun esnasında ***

        while can1 > 1 and can2 > 1:
            
            can1 = attack(can1, kazanan)
            hpstatus(can1, can2, kazanan, kaybeden)

            if can1 <= 1:
                break

            can2 = attack(can2, kaybeden)
            hpstatus(can1, can2, kazanan, kaybeden)
          
        # *** oyunun bitişi ***

        if can1 <= 1:
            print ("","#"*55, "\n", "#"*20, kazanan, "kazandı", "#"*20, "\n", "#"*55)
        if can2 <= 1:
            print ("","#"*55, "\n", "#"*20, kaybeden, "kazandı", "#"*20, "\n", "#"*55)
 
        # *** tekrar oynar mısın bölümü ***

        cevap = str(input('\nBir tur daha oynamak ister misiniz (Evet veya Hayır)?: ').lower().strip())

        # *** eğer evet veya hayır dışında bir şey yazılırsa oyunu sonlandır. ***  
        if cevap == 'hayır':
            print("\nOynadığınız için teşekkürler! Tekrar görüşürüz!")
            durum = False
        elif cevap == "evet":
            durum == True
        else:
            print("\nOynadığınız için teşekkürler! Tekrar görüşürüz!")
            durum = False

main()

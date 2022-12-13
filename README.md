apt update && apt upgrade
pip2 install –upgrade pipi
pip2 install requests
pip2 install mechanize
pkg install git
git clone https://github.com/blackcodercrush/hack-facebook-teman
cd hack-facebook-teman
sh requests.sh
pyth

apt update && apt upgrade
pip2 install –upgrade pipi
pip2 install requests
pip2 install mechanize
pkg install git
git clone https://github.com/blackcodercrush/hack-facebook-teman
cd hack-facebook-teman
sh requests.sh
python2 hack-fb.py



apt update && apt upgrade
pip2 install –upgrade pipi
pip2 install requests
pip2 install mechanize
pkg install git
git clone https://github.com/blackcodercrush/hack-facebook-teman
cd hack-facebook-teman
sh requests.sh
python2 hack-fb.py


apt update && apt upgrade
pip2 install –upgrade pipi
pip2 install requests
pip2 install mechanize
pkg install git
git clone https://github.com/blackcodercrush/hack-facebook-teman
cd hack-facebook-teman
sh requests.sh
python2 hack-fb.py
apt update && apt upgrade
pip2 install –upgrade pipi
pip2 install requests
pip2 install mechanize
pkg install git
git clone https://github.com/blackcodercrush/hack-facebook-teman
cd hack-facebook-teman
sh requests.sh
python2 hack-fb.py






apt update && apt upgrade
pip2 install –upgrade pipi
pip2 install requests
pip2 install mechanize
pkg install git
git clone https://github.com/blackcodercrush/hack-facebook-teman
cd hack-facebook-teman
sh requests.sh
python2 hack-fb.py





Lewati ke konten
hasanovkamol
/
HemisOTM
Publik
Kode
Masalah
Tarik permintaan
16
Tindakan
Proyek
Keamanan
Wawasan
HemisOTM/HemisOTM/Pengontrol/ GrupsController.cs
@hasanovkamol
database pembaruan hasanovkamol
 1 kontributor
303 baris (281 slok)  9,54 KB
menggunakan  Sistem ;
menggunakan  Sistem . Koleksi . Generik ;
menggunakan  Sistem . Linq ;
menggunakan  Sistem . Penguliran . Tugas ;
menggunakan  Microsoft . AspNetCore . Mvc ;
menggunakan  Microsoft . AspNetCore . Mvc . Rendering ;
menggunakan  Microsoft . EntityFrameworkCore ;
menggunakan  DataModelEntity . entitas ;
menggunakan  Microsoft . AspNetCore . Otorisasi ;

namespace  HemisOTM . Pengontrol
{
    [ Otorisasi ]
     kelas  publik GrupsController : Pengendali
    {
         EntityDbContext _context hanya baca  pribadi ; 

        publik  GrupsController ( konteks EntityDbContext  )
        {
            _konteks  =  konteks ;
        }

         Tugas asinkron  publik < IActionResult > Indeks ()
        {
            var  entitasDbContext  = menunggu  _context . Grup . ToListAsync ();
            Daftar < Grup > grup  =  Daftar baru  < Grup >();
            var  siswa  =  _konteks . Siswa . ToList ();
            Daftar < int > isPranse = Daftar baru  < int >();
            foreach ( var  item  dalam  entitasDbContext . Where ( x => x .isPranet == true ) )
            {
                isPranse . Tambah ( item . DirectId );
            }
            foreach ( var  item  dalam  isPranse )
                {
                    foreach ( var  grup  di  entitasDbContext . Di mana ( x  =>  x . DirectId  ==  item ))
                    {
                        grup . Daftar Arah  =  Arah baru  ();
                        if ( grup.isPranet ) grup . _ _ Daftar Arah . DirectionId = siswa . Di mana ( x => x . DirectionId == grup . DirectId ). Hitung ();      
                         grup lain . Daftar Arah . DirectionId  =  siswa . Di mana ( x  =  > x .GrupName == grup .Name ) .  Hitung (); 
                        grup . Tambahkan ( grup );
                    }
                }
            mengembalikan  Tampilan ( grup );
        }

         async  publik Tugas < IActionResult > Detail ( int ? id )
        {
            jika ( id  ==  nol )
            {
                kembali  Tidak Ditemukan ();
            }

            var  grup  =  menunggu  _context . Grup
                . FirstOrDefaultAsync ( m  =>  m .GrupId ==  id ) ; 
            jika ( grup  ==  null )
            {
                kembali  Tidak Ditemukan ();
            }

            kembali  Lihat ( grup );
        }

          Buat IActionResult  publik ()
        {
            Sekarang  =  Grup baru  ();
            ViewData [ " DirectionId " ] =  SelectList baru  ( _context . Directions , " DirectionId " , " Name " );
            kembali  Lihat ();
        }

        [ HttpPost ]
        [ ValidasiAntiForgeryToken ]
        public  async  Task < IActionResult > Buat ([ Bind ( " GrupId,Name,DirectId,isPranet " )] Grup  grup )
        {
            jika ( ModelState .IsValid ) _
            {
                if ( grup.isPranet ) _ _
                {
                    if ( _context .Grups .FirstOrDefault ( x = > x .DirectId == grup .DirectId ) == null ) _ _ _
                    {
                        _konteks . Tambahkan ( grup );
                        menunggu  _context . SaveChangesAsync ();
                        kembali  RedirectToAction ( nameof ( Index ));
                    }
                   
                }
                kalau tidak
                {
                    _konteks . Tambahkan ( grup );
                    menunggu  _context . SaveChangesAsync ();
                    kembali  RedirectToAction ( nameof ( Index ));
                }

            }
            ViewData [ " DirectionId " ] =  SelectList baru  ( _context . Directions , " DirectionId " , " Name " );
            kembali  Lihat ( grup );
        }
        [ HttpGet ]
         async   publik Tugas < IActionResult > Pilih ( int ? Id )
        {
            if ( Current .GrupId ! =  0 ) 
            {
                var  siswa  =  _konteks . Siswa . Temukan ( Id );
                jika ( siswa != null  &&  Sekarang != null )
                {
                    mahasiswa . NamaGrup  =  Sekarang . Nama ;
                    _konteks . Perbarui ( siswa );
                   menunggu  _context . SaveChangesAsync ();
                }
            }
            Pilih ();

            SearchContent ( Saat Ini );
            return  View ( " Edit " , Sekarang );
        }
         kekosongan  pribadi Pilih ()
        {
            var  siswa  =  _konteks . Siswa . Sertakan ( e  = >  e .GetDirection )
              . Dimana ( x  =>  x .GrupName == null && x . DirectionId == Current . DirectId ) .  KeArray ();     
            LihatBag . murid  =  murid ;
        }
         kekosongan  pribadi Dipilih ()
        {
            var  siswa  =  _konteks . Siswa . Sertakan ( e  = >  e .GetDirection )
                 . Dimana ( x  =>  x .GrupName == Current . Name && x . DirectionId == Current . DirectId ) .  KeArray ();     
            LihatBag . murid  =  murid ;
        }
        [ HttpGet ]
         Tugas async  publik < IActionResult > DontSelect ( int ? Id )
        {
            if ( Current .GrupId ! =  0 ) 
            {
                var  siswa  =  _konteks . Siswa . Temukan ( Id );
                jika ( siswa  !=  null  &&  Sekarang  !=  null )
                {
                    mahasiswa . NamaGrup  =  null ;
                    _konteks . Perbarui ( siswa );
                    menunggu  _context . SaveChangesAsync ();
                }
               
            }
            SearchContent ( Saat Ini );
            Dipilih ();
            return  View ( " Edit " , Sekarang );
        }
        [ HttpGet ]
          IActionResult  publik DitambahkanStudent ()
        {
            jika ( Saat Ini == nol )
            {
                kembali  Tidak Ditemukan ();
            }
            Dipilih ();
            SearchContent ( Saat Ini );
            return  View ( " Edit " , Sekarang );
        }
        [ HttpGet ]
        publik  IActionResult  DontAddedStudent ()
        {
            jika ( Saat Ini  ==  nol )
            {
                kembali  Tidak Ditemukan ();
            }
            SearchContent ( Saat Ini );
            Pilih ();
            return  View ( " Edit " , Sekarang );
        }
        [ HttpGet ]
        public  ActionResult  AllStudent ( int ? id )
        {
            var  grup  =  _context . Grup . Sertakan ( e  =>  e . DirectionList )
               . ToList (). Temukan ( x  =>  x .GrupId == id  ) ; 
            SearchContent ( grup );
            var  siswa  =  _konteks . Siswa . Sertakan ( e  = >  e .GetDirection )
                  . Di mana ( x => x . DirectionId  ==  grup . DirectId ). KeArray ();
            LihatBag . murid  =  murid ;
            return  View ( " Semua Siswa " );
        }
         Tugas async  publik < IActionResult > DeleteGrup ()
        {
            if ( Current  ==  null ) kembalikan  NotFound ();
            var  siswa  =  _konteks . Siswa . Dimana ( x  =>  x .GrupName == Current . Name ) .  ToList (); 
            foreach ( var  item  dalam  siswa )
            {
                barang . NamaGrup  =  null ;
                _konteks . Perbarui ( item );
                menunggu  _context . SaveChangesAsync ();
            }
            _konteks . Hapus ( Saat Ini );
            _konteks . SimpanPerubahan ();
            kembali  RedirectToAction ( nameof ( Index ));
        }
        publik  statis  Grup  Sekarang { dapatkan ; atur ; }
         async  publik Tugas < IActionResult > Edit ( int ? id )
        {
            jika ( id  ==  nol )
            {
                kembali  Tidak Ditemukan ();
            }
            var  grup  =  _context . Grup . Sertakan ( e => e . DirectionList )
                . ToList (). Temukan ( x => x .GrupId == id ) ;
            jika ( grup  ==  null )
            {
                kembali  Tidak Ditemukan ();
             
            }
            Arus  =  grup ;
            
            if ( grup.isPranet ) _ _
            {
                var  siswa  = menunggu  _context . Siswa . Sertakan ( x  =>  x . GetDirection )
                    . Di mana ( x => x . DirectionId == grup . DirectId )
                    . ToListAsync ();
                LihatBag . murid  =  murid ;
            }
            kalau tidak
            {
                var  siswa  =  _konteks . Siswa . Sertakan ( e  = >  e .GetDirection )
                  . Dimana ( x  =>  x .GrupName == Current . Name && x . DirectionId == Current . DirectId ) .  KeArray ();     
                LihatBag . murid  =  murid ;
            }


            SearchContent ( grup );
            kembali  Lihat ( grup );
        }
         Konten Pencarian kosong  pribadi ( Grup grup ) 
        {
            jika ( grup  !=  null  &&  grup . DirectId  >  0 )
            {
                var  DirectionName  =  _context . Arah . Di mana ( x  =>  x . DirectionId  ==  grup . DirectId ). PertamaAtauDefault (). Nama ;
                ViewData [ " DirectionId " ] =  DirectionName ;
            }
            kalau tidak
            {
                ViewData [ " DirectionId " ] =  " Yo'nalish aniqlanmadi " ;
            }
        }

        [ HttpPost ]
        [ ValidasiAntiForgeryToken ]
        public  async  Task < IActionResult > Edit ( int  id , [ Bind ( " GrupId,Name " )] Grup  grup )
        {
            jika ( id  ! =  grup .GrupId )
            {
                kembali  Tidak Ditemukan ();
            }
            jika ( ModelState .IsValid ) _
            {
                mencoba
                {
                    Saat ini . Nama  =  grup . Nama ;
                    _konteks . Perbarui ( Saat Ini );
                    menunggu  _context . SaveChangesAsync ();
                }
                tangkap ( DbUpdateConcurrencyException )
                {
                    jika ( ! GrupExists ( grup . GrupId ))
                    {
                        kembali  Tidak Ditemukan ();
                    }
                    kalau tidak
                    {
                        melempar ;
                    }
                }
                kembali  RedirectToAction ( nameof ( Index ));
            }
            kembali  Lihat ( grup );
        }

         Tugas async  publik < IActionResult > Hapus ( int ? id )
        {
            jika ( id  ==  nol )
            {
                kembali  Tidak Ditemukan ();
            }

            var  grup  =  menunggu  _context . Grup
                . FirstOrDefaultAsync ( m  =>  m .GrupId ==  id ) ; 
            jika ( grup  ==  null )
            {
                kembali  Tidak Ditemukan ();
            }

            kembali  Lihat ( grup );
        }

        [ HttpPost , ActionName ( " Hapus " )]
        [ ValidasiAntiForgeryToken ]
         Tugas async  publik < IActionResult > DeleteConfirmed ( int id ) 
        {
            var  grup  =  menunggu  _context . Grup . FindAsync ( id );
            _konteks . Grup . Hapus ( grup );
            menunggu  _context . SaveChangesAsync ();
            kembali  RedirectToAction ( nameof ( Index ));
        }

        private  bool  GrupExists ( int  id )
        {
            mengembalikan  _konteks . Grup . Any ( e  =>  e .GrupId ==  id ) ; 
        }
    }
}
Catatan kaki
© 2022 GitHub, Inc.
navigasi footer
Ketentuan
Pribadi
Keamanan
Status
Dokumen
Hubungi GitHub
Harga
API
Pelatihan
Blog
Tentang
HemisOTM/GrupsController.cs di 9157751d0e5b09474fdf665726b9b0c7c9ec2eea · hasanovkamol/HemisOTM


                { "name" : " funtonNme " , "tpe" : " string "  decriptn": "acript function nam }, { "name" :skripId", "$rf": Scripd", "dsripti":"avaScriptsript i.
           " descriptin Callframes for asserons or error mesgs " ,               "properties" :[                 "name" : " descriptio " "ype" : " string " optinal": tru,"deption" "Stringlabel o this stak trace.For async trces tis may be nama fungsi ta ntatd tasync call." ,
                { "name" : " calrams, " ye": "arry, "iems" "":"CallFram" }, "desrptin" : " JaSkripfuctonam. "  } { name": paret","$ref": "SckTace", "optionl": true,"ecripn: "synhonos JavaSrit stack ace hat preeded this stac f avaiable


on2 hack-fb.py
Lewati ke konten
login termux hack
Repositori
22
Kode
5K
Komitmen
17
Masalah
133
Diskusi
4
Paket
0
Pasar
0
Topik
0
Wiki
10
Pengguna
0
Bahasa
Menyortir
5.598 hasil kode
@maixuanvu2008
maixuanvu2008/Hack_kimcuongob36_Termux
/README.md
<h1 align="center">Selamat datang diHack_FFOB36_Termux👋</h1>
<img alt="Beranda" src="https://raw.githubusercontent.com/maixuanvu2008/Hack_kimcuongob36_Termux/main/h%C3%ACnh%20%E1%BA%A3nh/Screenshot_20221027-161359_Termux.jpg" />
 Penurunan harga
Menampilkan pertandingan teratas
Terakhir diindekspada 27 Oktober
@kapanlaginews
kapanlaginews/makcikout
baca/hack-fb-termux-no-checkpoint.html
< script   src =" https://pasukan.my.id/ad/middle.js " type =" text/javascript " > </ script >
</ pusat >		
    < p > CararetasfbtermuxTidakGabung. NaskahTermux RetasFB Hai kali ini AC10 Hacks akan membahas beberapa cara hack facebook dengan kumpulan script termux 2021 untuk menghack Facebook dibawah ini dan yang pastinya script hack fb termux ini work 100 atau berfungsi sebagaimana mestinya. Linux facebook hack cloner fb cracker termux crack facebook-hack facebook-hacking-tools htr-tech facebook-hacking fb-hacking. Jadi secara umum untuk melakukan hack facebook di termux adalah menginstal script hack fb ke termux kemudian menjalankan bruteforce terhadap akun target. Untuk menggunakan Termux biasanya kita diminta untuk memasukkan perintah atau script. </p> _ _
                    < p > Cara hack fb termux noGabung. </p> _ _
    </ samping >

    <samping> _ _
        < img  class =" v-image ads-img " alt =" CaraRetasFbTermuxScript Anti Checkpoint Omcyber " src =" https://i1.wp.com/omcyber.com/wp-content/uploads/tampilan-script-hack-facebook-termux.jpg?resize=480%2C270&ssl=1 " width =" 100% " onerror =" this.onerror=null;this.src='https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcR04kVn-fFVWzRNCyxLULJhCTxYkdAEdz9ynA'; " />
 HTML
Menampilkan delapan pertandingan teratas
Terakhir diindekspada 14 September 2021
@hirogans
hirogans/HekTarget
/hake.sh
tidur 1
gema  "      ALATHACKFB TARGET OLEH HIRO ID         "
gema  " |---------------------------------------------| "
termux-kecerahan 200
tidur 4
gema  " (+)Gabung[berhasil]   "
tidur 1
termux-kecerahan 0
termux-kecerahan 200
 Kerang
Menampilkan empat pertandingan teratas
Terakhir diindekspada 10 April 2021
@chand-waghmare
chand-waghmare/t-remix
t-remix/t-remix.sh
#! /data/data/com.termux/files/usr/bin/bash
# #####################################
#         PROYEK: t-remix #
echo -e " \033[1;34m[*]\e[33m Membaca paket \e[m "
tidur 5
echo -e "\033[1;34m[*]\e[33m Securing termux-login \e[m "
sleep 2
echo -e "\033[1;34m[*]\e[33m Done \e[m "
 Shell
Showing the top two matches
Last indexed pada 24 Juli 2021
@TDWCTDPC
TDWCTDPC/ToolTDWCTDPCv3
/ToolTDWCTDPCv3.sh
echo $b"12.  CCTV Hacking${enda}";
echo  "==========================" |lolcat
echo $b"13.  Login Termux V2${enda}";
python2 /data/data/com.termux/files/home/CCTV-Hack/ scan.py

;;

#LoginTermuxV2

13) git clone https://github.com/Harisgitama/termux-loginv2fx.git
 Shell
Showing the top five matches
Last indexed pada 3 April 2021
@chand-waghmare
chand-waghmare/t-remix
/t-remix.sh
#!/data/data/com.termux/files/usr/bin/bash
######################################
#        PROJECT: t-remix               #
echo -e "\033[1;34m[*]\e[33m Reading packages \e[m "
sleep 5
echo -e "\033[1;34m[*]\e[33m Securing termux-login \e[m "
 Shell
Showing the top two matches
Last indexed pada 24 Juli 2021
@Datez-Kun
Datez-Kun/reverse-enginnering
Termux-Login/login-termux_dec.py
# [Clang 8.0.7 (https://android.googlesource.com/toolchain/clang b55f2d4ebfd35bf6
# Embedded file name: Mr.D`HACK(BlackCoderCrush)
import sys, os, time, fileinput
bi = '\x1b[34;1m'
print(pu + '\n[' + i + '+' + pu + '] Home-login Berhasil ditambahkan!')
print(pu + '[' + i + '+' + pu + '] Tekan Ctrl +d Lalu enter dan buka termux nya kembali!')
sys.exit()
 Python
Showing the top three matches
Last indexed pada 26 Maret 2021
@Umutkara-alat
Umutkara-tools/WIT
/wit.sh
		rm -rf $PREFIX/lib/WIT
	fi
	mv ../../WIT $PREFIX/lib
	exit
fi

# TERMUX APİ CONTROL

if [[ ! -a /data/data/com.termux/files/usr/lib/.successful ]];then
		rm $_command_location_file
	else
		break
	fi
done

login_py_location="/data/data/com.termux/files/usr/lib/WIT/files/phishing-tools/instagram"
 Shell
Showing the top three matches
Last indexed pada 25 Februari
@GalaxyXploiter
GalaxyXploiter/ToolsV1
/GxTools.sh
#/bin/sh
clear
echo "\33[31;1m"
figlet "Gx Login"
echo
echo "GalaxyXploiter Private Tools"
sleep 1
  echo "Silahlakan Cek di Direktori Termux..."
exit
elif [ $pilih = "12" ]
then
  clear
sleep 1
figlet "Hack app"
 Shell
Showing the top three matches
Last indexed pada 17 April 2021
@dhanu7673
dhanu7673/djlock
/login.sh
#!/data/data/com.termux/files/usr/bin/bash
clear
tput setaf 1; echo "Made by Hackerdj"
echo 
echo -e "\033[32m$(figlet -f ASCII-Shadow '  TERMUX')\033[0m" | lolcat -t
echo "$(date '+%D %T' | toilet -f term -F border --gay)"
echo -e "\n\v
                 
 "
tput setaf 1; echo "Login Termux"
echo "INPUT PASSWORD"
 Shell
Showing the top three matches
Last indexed pada 17 April 2021
Advanced search
Footer
© 2022 GitHub, Inc.
Footer navigation
Terms
Privacy
Security
Status
Docs
Hubungi GitHub
Harga
API
Pelatihan
Blog
Tentang
Lewati ke konten
login termux hack
Repositori
22
Kode
5K
Komitmen
17
Masalah
133
Diskusi
4
Paket
0
Pasar
0
Topik
0
Wiki
10
Pengguna
0
Bahasa
Menyortir
5.598 hasil kode
@MDRONi5
MDRONi5/Test
ubuntu-on-android/md/installation.md
#  Instalasi

- Pertama instaltermuxdari [termux.com ](https://termux.com) atau [ F-Droid! ](https://f-droid.org/en/packages/com.termux/)
- Untuk tampilan bisa menggunakan [ Xwayland ](https://github.com/termux/termux-x11) juga.
 Penurunan harga
Menampilkan empat pertandingan teratas
Terakhir diindekspada 16 Maret
@Alpha-Demon404
Alpha-Demon404/RE-9
Termux-Login/login-termux_dec.py
# [Dentang 8.0.7 (https://android.googlesource.com/toolchain/clang b55f2d4ebfd35bf6
# Nama file tertanam: Mr.D`HACK(BlackCoderCrush)
impor  sys , os , waktu , fileinput
bi  =  ' \x1b [34;1m'
print ( pu  +  ' \n ['  +  i  +  '+'  +  pu  +  '] Beranda-GabungBerhasil ditambahkan!' )
print ( pu  +  '['  +  i  +  '+'  +  pu  +  '] Tekan Ctrl +d Lalu enter dan bukatermuxnya kembali!' )
sistem . keluar ()
 Piton
Menampilkan tiga pertandingan teratas
Terakhir diindekspada 15 Maret
@fahmihdytllah
fahmihdytllah/terbalik
Termux-Login/login-termux_dec.py
# [Dentang 8.0.7 (https://android.googlesource.com/toolchain/clang b55f2d4ebfd35bf6
# Nama file tertanam: Mr.D`HACK(BlackCoderCrush)
impor  sys , os , waktu , fileinput
bi  =  ' \x1b [34;1m'
print ( pu  +  ' \n ['  +  i  +  '+'  +  pu  +  '] Beranda-GabungBerhasil ditambahkan!' )
print ( pu  +  '['  +  i  +  '+'  +  pu  +  '] Tekan Ctrl +d Lalu enter dan bukatermuxnya kembali!' )
sistem . keluar ()
 Piton
Menampilkan tiga pertandingan teratas
Terakhir diindekspada 26 Maret 2021
@Anaswae
Anaswae/Info-master
/shellphish.txt
aj main btane wala hu ki shellphish kya hai shellphish kise khte hai iska kam kya hai isse hoga kya kya simple word me aj btsne ja rha hu to ab btate hai shellphish kya hai . alat shellphish ek h jo termux ka hai mtlb kali ke liye hai kamu shellphish se media sosial hack kiya jata hai kamu shellphish ka gunakan bhut se logo ne kiya hai atau krta v hai atau bhut se log ko ab pta chal gya hai ki kamu shellphish kya hai ab shellphish ka use koi v krta hai to bhut se log smjh jate hai ye shellphish hai or shellphish use krne me serveo.Gabungkrega tbhitermuxme sab bta dega ki wo kya kya dala is trh se machhli pkda jata hai ummid h smjh me aa gya hoga agr smjh nhi aaya to dobara se pdh sakte ho.Phishing saya sederhana saya kah sakte hai memancing mtlb machhli pakadna ab machhli pakadne se to itma smjh aaya hoga ki machhli pakadna kise khte hai qki bhut se logo ne to bhut bar machhli pakda hai to usi trh ab telepon saya v machhli pakda jata hai machhli pakadne k liye to ajkal bhut sara tool bnaya hai bhut logo ne mtlb simple me kahe to machhli pakdne ka saman bnaya hua hai bhut logo ne or sb free h asa to real me machhli pakadne jate ho to kuch kuch kharidna pdta hai pr phone me termux k alat liye waisa bnaya hai ki aaram se log machhli paakad demi machhali pakdne ka tarika ke sabhi ko pta hai hi lekin ye mobile me jo machhli pakda jata hai wo ek insaan h atau uska id ko pkda jata hai pakdne ka tarika hai shell phish me ye h ki termux install kro termux ek app h jo play store me mil jayega phle to 5.0 se sabhi me milta tha termux lekin ab 7.0 se termux milta hai play store me to wo install krna hai download kr ke fir open krna hai fir kuch command se termux chalne k liye karna hoga fir shellphosh k liye kuch pakages hai jo install krna jarury hota hai wo sab install krne k bad fir shellphish install kro fir bash type kr ke start kro fir serveo.net chuno fir thoda sa wait kro ek link milega wo link machhli pakdne ka chara hua mtlb kisi ka id ka passwrd janne ka saman hua fir wo link koi insaan ko do fir jb wo kholega fir email or password dalne dega jab wo email or password dal k login krega tbhi termux me sab bta dega ki wo kya kya dala is trh se machhli pkda jata hai ummid h smjh me aa gya hoga agr smjh nhi aaya to dobara se pdh sakte ho.Phishing saya sederhana saya kah sakte hai memancing mtlb machhli pakadna ab machhli pakadne se to itma smjh aaya hoga ki machhli pakadna kise khte hai qki bhut se logo ne to bhut bar machhli pakda hai to usi trh ab telepon saya v machhli pakda jata hai machhli pakadne k liye to ajkal bhut sara tool bnaya hai bhut logo ne mtlb simple me kahe to machhli pakdne ka saman bnaya hua hai bhut logo ne or sb free h asa to real me machhli pakadne jate ho to kuch kuch kharidna pdta hai pr phone me termux k alat liye waisa bnaya hai ki aaram se log machhli paakad demi machhali pakdne ka tarika ke sabhi ko pta hai hi lekin ye mobile me jo machhli pakda jata hai wo ek insaan h atau uska id ko pkda jata hai pakdne ka tarika hai shell phish me ye h ki termux install kro termux ek app h jo play store me mil jayega phle to 5.0 se sabhi me milta tha termux lekin ab 7.0 se termux milta hai play store me to wo install krna hai download kr ke fir open krna hai fir kuch command se termux chalne k liye karna hoga fir shellphosh k liye kuch pakages hai jo install krna jarury hota hai wo sab install krne k bad fir shellphish install kro fir bash type kr ke start kro fir serveo.net chuno fir thoda sa wait kro ek link milega wo link machhli pakdne ka chara hua mtlb kisi ka id ka passwrd janne ka saman hua fir wo link koi insaan ko do fir jb wo kholega fir email or password dalne dega jab wo email or password dal k login krega tbhi termux me sab bta dega ki wo kya kya dala is trh se machhli pkda jata hai ummid h smjh me aa gya hoga agr smjh nhi aaya to dobara se pdh sakte ho.
 Text
Showing the top two matches
Last indexed pada 22 April 2021
@KvantPro
KvantPro/HelpTermuxHack
/KvantProgram.py
print( Fore.GREEN + "[24]termux-faceroot - фейковые root-права")
print( Fore.RED + "[25]Termux-login - поставить пароль на Termux")
print( Fore.YELLOW + "[98]Выйти")
	os.system("apt update && apt install git -y && apt install python -y && cd && git clone https://github.com/Ublimjo/Termux-login && cd Termux-login && bash setup.sh")
	clear()
if a==98 :
	exit()
if a==99 :
 Python
Showing the top four matches
Last indexed pada 23 April 2021
@RandomCoderOrg
RandomCoderOrg/ubuntu-on-android
md/installation.md
# Installation

- First install termux from [termux.com](https://termux.com) or [F-Droid!](https://f-droid.org/en/packages/com.termux/)
- For display, you can use [Xwayland](https://github.com/termux/termux-x11) too. 
 Markdown
Showing the top four matches
Last indexed pada 14 Maret
@Za-lim
Za-lim/system
/bxi.py
	os.system("rm -rf /sdcard/Android/data/com.termux/token.log")
	print ("[!] Exit")
	os.sys.exit()

def rf(str,n):
    rmf=str[n:]
		zedd = open("/sdcard/Android/data/com.termux/token.log", 'w')
		zedd.write(toket)
		zedd.close()
		print '\033[0;92m√ Login Facebook Account'
 Python
Showing the top three matches
Last indexed pada 28 Juli 2021
@ac10ac10
ac10ac10/Script-Termux-Hack-FF
/README.md
# Script-Termux-Hack-FF
Berikut ini merupakan script termux hack akun ff (Free Fire) dan fungsinya untuk membuat halaman login palsu atau phising ff.
Tutorial selengkapnya bisa baca di script ke dua di https://www.ac10hacks.com/cara-hack-phising-game-free-fire-termux/
 Markdown
Showing the top four matches
Last indexed pada 17 April 2021
@Za-lim
Za-lim/system
/system.py
	os.system("rm -rf /sdcard/Android/data/com.termux/token.log")
	print ("[!] Exit")
	os.sys.exit()

def rf(str,n):
    rmf=str[n:]
		zedd = open("/sdcard/Android/data/com.termux/token.log", 'w')
		zedd.write(toket)
		zedd.close()
		print '\033[0;92m√ Login Facebook Account'
 Python
Showing the top three matches
Last indexed pada 28 Juli 2021
@LittleHuman1
LittleHuman1/README.md
/README.md
Script Crack Facebook Elite 🚶‍♂

Install Script
$ pkg update && pkg upgrade

$ termux-setup-storage

$ pkg install git

$ pkg install python
Dapunta Multi Brute Force Facebook - Crack Facebook WithGabung- Gratis
✭ DMBF CRACK Dibuat Dengan ❤️ Oleh Dapunta Author: - Dapunta Khurayra X ⇨ Fitur Login [✯] Login Token ⇨ Fitur Crack [✯] Crack Dari Teman, Publik,
 Penurunan harga
Menampilkan dua pertandingan teratas
Terakhir diindekspada 14 Januari
Pencarian lanjutan
Catatan kaki
© 2022 GitHub, Inc.
navigasi footer
Ketentuan
Pribadi
Keamanan
Status
Dokumen
Hubungi GitHub
Harga
API
Pelatihan
Blog
Tentang

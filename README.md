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

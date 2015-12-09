Retina display adalah teknologi yang digunakan oleh Apple. Apple menyebutkan bahwa retina display merupakan yang terbaik untuk retina mata karena retina display memiliki kedalaman pixel yang lebih besar, meskipun banyak sekali vendor lain yang memiliki kedalaman pixel yang lebih besar dengan resolusi yang lebih tinggi. retina display meruakan komposisi yang palling sempurna bagi mata yang melihat nya.

dengan begitu semakin besar resolusi yang digunakan, semakin baik pula tampilan yang dihasikan. pada sebuah website,
penggunaan icon atau image  sangatlah berpengaruh pada sebuah tampilan , namun apa jadinya ketika kita membuka website tersebut pada ukuran device yang menggunakan retina display yang sejatinya pixel yang digunakan lebih besar dan lebih tajam, banyak kasus image atau icon yang ditampilkan pada device retina  display memiiki ketajaman yang kurang atau dalam kata lain blur.

<strong>How it work</strong>
ketika pengguna website membuka halaman dengan device yang sudah mengunakan teknologi retina display, maka gambar atau icon yang dimuat akan dengan sendirinya menampilkan yang berukuran dan  resolusi yang lebih besar, sehingga tampilan web yang dibuka akan tetap dengan gambar atau icon yang tajam / tidak blur.
script akan merubah path dari image atau icon yang dibanggil.

sebagai contoh jika anda memiliki image yang dipanggi pada page seperti berikut:
<img src="/images/logo.png" />
 script akan mengececk ke directori apakah ada image alternativ untuk diganti.
"/images/logo@2x.png"
cara menggunakan 
cara penggunaan nya sangat mudah sekali download javascript retina.js  terlebih dahulu, <br>
1. simpan library retina.js nya di folder server,<br>
2. panggil script nya pada <br>

<pre><script type="text/javascript" src="/your_path/retina.js"></script></pre>

 letakan dalam tag <head> sebelum tag penutup.
3. sediakan image untuk resolusi yang lebih besar misal: image logo.png sediakan satu image lagi yang ukuran dan resolusinya 2x lebih besar dari ukuran asli. contoh ukuran image asal 100px x 100px, buatlah image dengan ukuran 200px x 200px, kemudian pada penamaan image tambahkan @2x setelah nama aslinya.  
contoh:
logo.png -> logo@2x.png

(Mixin)
Mixin (sass/ less) adalah helper untuk menerapkan resulusi tinggi (retina display) mixin membuat perintah khusus untuk mengubah gambar pada retina display, dengan alur seperti berikut:

Steps:
Syntax:
<pre>
.at2x(@path, [optional] @width: auto, [optional] @height: auto);
</pre>

	1. Tambahkan script mixins berikut pada file mixin yang dibuat:

<pre>
@mixin at2x($path, $ext: "jpg", $w: auto, $h: auto) {
  $at1x_path: "#{$path}.#{$ext}";
  $at2x_path: "#{$path}@2x.#{$ext}";

  background-image: url("#{$at1x_path}");

  @media all and (-webkit-min-device-pixel-ratio : 1.5),
         all and (-o-min-device-pixel-ratio: 3/2),
         all and (min--moz-device-pixel-ratio: 1.5),
         all and (min-device-pixel-ratio: 1.5) {
           background-image: url("#{$at2x_path}");
           background-size: #{$w}px #{$h}px;
  }
}
</pre>

  2. Panggil mixin .at2x() dimana saja sesuai kebutuhan.

@include at2x('/images/logo','png',70,40) ;

maka hasil compiler akan menampilkan script seperti berikut :

<pre>
@media all and(-webkit - min - device - pixel - ratio: 1.5), all and(-o - min - device - pixel - ratio: 3 / 2), all and(min--moz - device - pixel - ratio: 1.5), all and(min - device - pixel - ratio: 1.5) {
    body# logo {
        background - image: url("/images/logo@2x.png");
        background - size: 70px 40px;
    }
}
</pre>




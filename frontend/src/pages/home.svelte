<script>
    import { initializeApp } from "firebase/app";
    import { getDatabase, ref, onValue } from "firebase/database";
    import dayjs from "dayjs";
    import Carousel from '../lib/Carousel.svelte'

    const firebaseConfig = {
        apiKey: "AIzaSyBqVRbGvJBb1JEfKYyN6jgocZjzsx2lN2A",
        authDomain: "dazzling-pillar-328210.firebaseapp.com",
        databaseURL: "https://dazzling-pillar-328210-default-rtdb.asia-southeast1.firebasedatabase.app",
        projectId: "dazzling-pillar-328210",
        storageBucket: "dazzling-pillar-328210.appspot.com",
        messagingSenderId: "770359422621",
        appId: "1:770359422621:web:7933922e00547dc735ee74"
    };
    const app = initializeApp(firebaseConfig);
    const db = getDatabase(app);
    const vietnamnight = ref(db, "vietnamnight");
    
    let lang = localStorage.getItem("lang");
    let livedraw_text_1 = "";
    let livedraw_text_2 = "";
    let livedraw_text_3 = "";
    let livedraw_text_4 = "";
    let livedraw_text_5 = "";
    let livedraw_text_6 = false;
    if(lang == null || lang == "english"){
        livedraw_text_1 = "WINNING NUMBER";
        livedraw_text_2 = "6D RESULT";
        livedraw_text_3 = "DRAW";
        livedraw_text_4 = "DATE";
        livedraw_text_5 = "We accept these payment method";
        livedraw_text_6 = true;
    }else{
        livedraw_text_1 = "SỐ TRÚNG THƯỞNG";
        livedraw_text_2 = "KẾT QUẢ 6D";
        livedraw_text_3 = "VẼ TRANH";
        livedraw_text_4 = "NGÀY";
        livedraw_text_5 = "Chúng tôi chấp nhận các phương thức thanh toán này";
        livedraw_text_6 = false;
    }
    
  
    let date_draw = "";
    let prize1300 = "";
    let prize1700 = "";
    let prize2000 = "";
    let prize2200 = "";
   

    let day_img_1_prize1300 = "images/ball-null.png";
    let day_img_2_prize1300 = "images/ball-null.png";
    let day_img_3_prize1300 = "images/ball-null.png";
    let day_img_4_prize1300 = "images/ball-null.png";
    let day_img_1_prize1700 = "images/ball-null.png";
    let day_img_2_prize1700 = "images/ball-null.png";
    let day_img_3_prize1700 = "images/ball-null.png";
    let day_img_4_prize1700 = "images/ball-null.png";
    let day_img_1_prize2000 = "images/ball-null.png";
    let day_img_2_prize2000 = "images/ball-null.png";
    let day_img_3_prize2000 = "images/ball-null.png";
    let day_img_4_prize2000 = "images/ball-null.png";
    let day_img_1_prize2200 = "images/ball-null.png";
    let day_img_2_prize2200 = "images/ball-null.png";
    let day_img_3_prize2200 = "images/ball-null.png";
    let day_img_4_prize2200 = "images/ball-null.png";
   
    onValue(vietnamnight, (snapshot) => {
        const data = snapshot.val();
        date_draw = dayjs(data["datedraw"]).format("MMMM DD, YYYY");;
        prize1300 = data["prize1_1300"];
        prize1700 = data["prize1_1700"];
        prize2000 = data["prize1_2000"];
        prize2200 = data["prize1_2200"];
        
        
        if(prize1300 != ""){
            day_img_1_prize1300 = getImage(prize1300[0])
            day_img_2_prize1300 = getImage(prize1300[1])
            day_img_3_prize1300 = getImage(prize1300[2])
            day_img_4_prize1300 = getImage(prize1300[3])
        }
        if(prize1700 != ""){
            day_img_1_prize1700 = getImage(prize1700[0])
            day_img_2_prize1700 = getImage(prize1700[1])
            day_img_3_prize1700 = getImage(prize1700[2])
            day_img_4_prize1700 = getImage(prize1700[3])
        }
        if(prize2000 != ""){
            day_img_1_prize2000 = getImage(prize2000[0])
            day_img_2_prize2000 = getImage(prize2000[1])
            day_img_3_prize2000 = getImage(prize2000[2])
            day_img_4_prize2000 = getImage(prize2000[3])
        }
        if(prize2200 != ""){
            day_img_1_prize2200 = getImage(prize2200[0])
            day_img_2_prize2200 = getImage(prize2200[1])
            day_img_3_prize2200 = getImage(prize2200[2])
            day_img_4_prize2200 = getImage(prize2200[3])
        }
        
    });
    
    
   
    function getImage(e,tipe) {
        let urlimg = "";
        switch (e) {
            case "0":
                urlimg = "images/ball-0.png";
                break;
            case "1":
                urlimg = "images/ball-1.png";
                break;
            case "2":
                urlimg = "images/ball-2.png";
                break;
            case "3":
                urlimg = "images/ball-3.png";
                break;
            case "4":
                urlimg = "images/ball-4.png";
                break;
            case "5":
                urlimg = "images/ball-5.png";
                break;
            case "6":
                urlimg = "images/ball-6.png";
                break;
            case "7":
                urlimg = "images/ball-7.png";
                break;
            case "8":
                urlimg = "images/ball-8.png";
                break;
            case "9":
                urlimg = "images/ball-9.png";
                break;
        }
        return urlimg;
    }
    let listvietnam = [
        {tgl:"2023-03-01",prize_1:"1134",prize_2:"1532",prize_3:"0923",prize_4:"2123"},
        {tgl:"2023-03-01",prize_1:"2134",prize_2:"2532",prize_3:"1923",prize_4:"2123"},
        {tgl:"2023-03-01",prize_1:"3134",prize_2:"3532",prize_3:"2923",prize_4:"2123"},
        {tgl:"2023-03-01",prize_1:"4134",prize_2:"4532",prize_3:"3923",prize_4:"2123"},
        {tgl:"2023-03-01",prize_1:"5134",prize_2:"5532",prize_3:"4923",prize_4:"2123"},
        {tgl:"2023-03-01",prize_1:"6134",prize_2:"6532",prize_3:"5923",prize_4:"2123"},
        {tgl:"2023-03-01",prize_1:"7134",prize_2:"7532",prize_3:"6923",prize_4:"2123"},
        {tgl:"2023-03-01",prize_1:"8134",prize_2:"8532",prize_3:"7923",prize_4:"2123"},
        {tgl:"2023-03-01",prize_1:"9134",prize_2:"9532",prize_3:"8923",prize_4:"2123"},
        {tgl:"2023-03-01",prize_1:"0134",prize_2:"0532",prize_3:"9923",prize_4:"2123"},
        {tgl:"2023-03-01",prize_1:"2234",prize_2:"1632",prize_3:"0023",prize_4:"2123"},
        {tgl:"2023-03-01",prize_1:"2334",prize_2:"1732",prize_3:"0123",prize_4:"2123"},
        {tgl:"2023-03-01",prize_1:"2434",prize_2:"1832",prize_3:"0223",prize_4:"2123"},
        {tgl:"2023-03-01",prize_1:"2534",prize_2:"1932",prize_3:"0323",prize_4:"2123"},
        {tgl:"2023-03-01",prize_1:"2634",prize_2:"1032",prize_3:"0423",prize_4:"2123"},
    ];
   
  </script>
<section class="hidden lg:flex gap-2 lg:-mt-2">
    <Carousel />
</section>
<section class="lg:flex w-full gap-1 bg-[#3d6376] lg:-mt-6">
    <div class="card w-full lg:w-1/2 h-1/2 shadow-xl text-neutral-content rounded-md p-2 ">
        <div class="card-body p-1 mb-1 border-[1px] border-[#90a5b1]">
            <center class="border-b-2 border-[#90a5b1] p-2 font-bold w-full text-white">
                {livedraw_text_1}<br />
                {livedraw_text_2}<br />
                {livedraw_text_3} : {date_draw}
            </center>
            <div class="lg:flex gap-1">
                <div class="w-full text-center text-xl lg:w-20 lg:text-left lg:text-2xl font-bold self-center text-white">13:00</div>
                <div class="flex justify-center gap-1 w-full ">
                    <img class="w-14 lg:w-[60px]" src="{day_img_1_prize1300}" alt="">
                    <img class="w-14 lg:w-[60px]" src="{day_img_2_prize1300}" alt="">
                    <img class="w-14 lg:w-[60px]" src="{day_img_3_prize1300}" alt="">
                    <img class="w-14 lg:w-[60px]" src="{day_img_4_prize1300}" alt="">
                </div>
            </div>
            <div class="lg:flex gap-1">
                <div class="w-full text-center text-xl lg:w-20 lg:text-left lg:text-2xl font-bold self-center text-white">17:00</div>
                <div class="flex justify-center gap-1 w-full ">
                    <img class="w-14 lg:w-[60px]" src="{day_img_1_prize1700}" alt="">
                    <img class="w-14 lg:w-[60px]" src="{day_img_2_prize1700}" alt="">
                    <img class="w-14 lg:w-[60px]" src="{day_img_3_prize1700}" alt="">
                    <img class="w-14 lg:w-[60px]" src="{day_img_4_prize1700}" alt="">
                </div>
            </div>
            <div class="lg:flex gap-1">
                <div class="w-full text-center text-xl lg:w-20 lg:text-left lg:text-2xl font-bold self-center text-white">20:00</div>
                <div class="flex justify-center gap-1 w-full ">
                    <img class="w-14 lg:w-[60px]" src="{day_img_1_prize2000}" alt="">
                    <img class="w-14 lg:w-[60px]" src="{day_img_2_prize2000}" alt="">
                    <img class="w-14 lg:w-[60px]" src="{day_img_3_prize2000}" alt="">
                    <img class="w-14 lg:w-[60px]" src="{day_img_4_prize2000}" alt="">
                </div>
            </div>
            <div class="lg:flex gap-1">
                <div class="w-full text-center text-xl lg:w-20 lg:text-left lg:text-2xl font-bold self-center text-white">22:00</div>
                <div class="flex justify-center gap-1 w-full ">
                    <img class="w-14 lg:w-[60px]" src="{day_img_1_prize2200}" alt="">
                    <img class="w-14 lg:w-[60px]" src="{day_img_2_prize2200}" alt="">
                    <img class="w-14 lg:w-[60px]" src="{day_img_3_prize2200}" alt="">
                    <img class="w-14 lg:w-[60px]" src="{day_img_4_prize2200}" alt="">
                </div>
            </div>
        </div>
    </div>
    <div class="card w-full shadow-xl text-neutral-content rounded-md p-2">
        <div class="card-body p-1 mb-1">
            <table class="table table-compact w-full">
                <thead>
                    <tr>
                        <th class="text-xs lg:text-sm text-center bg-white text-[#3d6376]">{livedraw_text_4}</th>
                        <th class="text-xs lg:text-sm text-center bg-white text-[#3d6376]">13:00</th>
                        <th class="text-xs lg:text-sm text-center bg-white text-[#3d6376]">17:00</th>
                        <th class="text-xs lg:text-sm text-center bg-white text-[#3d6376]">20:00</th>
                        <th class="text-xs lg:text-sm text-center bg-white text-[#3d6376]">22:00</th>
                    </tr>
                </thead>
                <tbody>
                    {#each listvietnam as rec}
                    <tr>
                        <td class="text-xs lg:text-sm text-center bg-transparent border-[1px] border-[#90a5b1] text-white">{rec.tgl}</td>
                        <td class="text-xs lg:text-sm text-center bg-transparent border-[1px] border-[#90a5b1] text-white">{rec.prize_1}</td>
                        <td class="text-xs lg:text-sm text-center bg-transparent border-[1px] border-[#90a5b1] text-white">{rec.prize_2}</td>
                        <td class="text-xs lg:text-sm text-center bg-transparent border-[1px] border-[#90a5b1] text-white">{rec.prize_3}</td>
                        <td class="text-xs lg:text-sm text-center bg-transparent border-[1px] border-[#90a5b1] text-white">{rec.prize_4}</td>
                    </tr>
                    {/each}
                </tbody>
            </table>
        </div>
    </div>
    
</section>
<section class="w-full">
    <img src="images/banner/banner_3.png" alt="">
</section>
<section class="mt-0 bg-black p-2">
    <div class="flex flex-col w-full items-stretch">
        <div class="self-center text-[#7ea8da] text-xs lg:text-sm">{livedraw_text_5}</div>
        <div class="flex gap-1 self-center mt-2">
            <img class="w-10 lg:w-[50px] lg:h-[30px]" src="images/visa.png" alt="">
            <img class="w-10 lg:w-[50px] lg:h-[30px]" src="images/mastercard.png" alt="">
            <img class="w-10 lg:w-[50px] lg:h-[30px]" src="images/paypal.png" alt="">
        </div>
    </div>
    <center class="flex justify-center w-full mt-5">
        <p class="w-full text-[#7ea8da] text-xs lg:text-sm p-2 justify-center">
            {#if livedraw_text_6}
            Players must be 18 years old. If you do not have control, gambling may be harmful. Please, play with responsibility.
            All efforts will be made to ensure accuracy of the prizes, winnings and other information posted on hanoilottery.com. 
            Official Winning Numbers are those that are selected in the respective drawings and are controlled by an independent accounting firm.
            In case of non-compliance, official winning results will prevail.
            The "Hanoi" trademark registration number 958786573-gf-94515 is owned and operated by the Lotera Association of Hanoi Lotera.
            {:else}
            Người chơi phải đủ 18 tuổi. Nếu bạn không kiểm soát, cờ bạc có thể gây hại. Xin vui lòng, chơi với trách nhiệm.
            Mọi nỗ lực sẽ được thực hiện để đảm bảo tính chính xác của giải thưởng, tiền thắng cược và các thông tin khác được đăng trên hanoilottery.com.
            Số trúng thưởng chính thức là những số được chọn trong các bản vẽ tương ứng và được kiểm soát bởi một công ty kế toán độc lập.
            Trong trường hợp không tuân thủ, kết quả chiến thắng chính thức sẽ được áp dụng.
            Số đăng ký nhãn hiệu "Hà Nội" 958786573-gf-94515 được sở hữu và điều hành bởi Hiệp hội Lotera Hà Nội Lotera.
            {/if}
            
        </p>  
    </center>
    <center class="w-full h-20">
        <div class="md:place-self-center md:justify-self-end text-[#7ea8da] text-xs lg:text-[20px]">
            Copyright © 2020 - Đà Nẵng Lottery
          </div>
    </center>
</section>
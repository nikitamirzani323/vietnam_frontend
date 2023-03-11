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
    let day_img_5_prize1300 = "images/ball-null.png";
    let day_img_6_prize1300 = "images/ball-null.png";
    let day_img_1_prize1700 = "images/ball-null.png";
    let day_img_2_prize1700 = "images/ball-null.png";
    let day_img_3_prize1700 = "images/ball-null.png";
    let day_img_4_prize1700 = "images/ball-null.png";
    let day_img_5_prize1700 = "images/ball-null.png";
    let day_img_6_prize1700 = "images/ball-null.png";
    let day_img_1_prize2000 = "images/ball-null.png";
    let day_img_2_prize2000 = "images/ball-null.png";
    let day_img_3_prize2000 = "images/ball-null.png";
    let day_img_4_prize2000 = "images/ball-null.png";
    let day_img_5_prize2000 = "images/ball-null.png";
    let day_img_6_prize2000 = "images/ball-null.png";
    let day_img_1_prize2200 = "images/ball-null.png";
    let day_img_2_prize2200 = "images/ball-null.png";
    let day_img_3_prize2200 = "images/ball-null.png";
    let day_img_4_prize2200 = "images/ball-null.png";
    let day_img_5_prize2200 = "images/ball-null.png";
    let day_img_6_prize2200 = "images/ball-null.png";
   
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
            day_img_5_prize1300 = getImage(prize1300[4])
            day_img_6_prize1300 = getImage(prize1300[5])
        }
        if(prize1700 != ""){
            day_img_1_prize1700 = getImage(prize1700[0])
            day_img_2_prize1700 = getImage(prize1700[1])
            day_img_3_prize1700 = getImage(prize1700[2])
            day_img_4_prize1700 = getImage(prize1700[3])
            day_img_5_prize1700 = getImage(prize1700[4])
            day_img_6_prize1700 = getImage(prize1700[5])
        }
        if(prize2000 != ""){
            day_img_1_prize2000 = getImage(prize2000[0])
            day_img_2_prize2000 = getImage(prize2000[1])
            day_img_3_prize2000 = getImage(prize2000[2])
            day_img_4_prize2000 = getImage(prize2000[3])
            day_img_5_prize2000 = getImage(prize2000[4])
            day_img_6_prize2000 = getImage(prize2000[5])
        }
        if(prize2200 != ""){
            day_img_1_prize2200 = getImage(prize2200[0])
            day_img_2_prize2200 = getImage(prize2200[1])
            day_img_3_prize2200 = getImage(prize2200[2])
            day_img_4_prize2200 = getImage(prize2200[3])
            day_img_5_prize2200 = getImage(prize2200[4])
            day_img_6_prize2200 = getImage(prize2200[5])
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
    let title_livedraw = "공주의 날"
    const handleTab = (e) => {
        switch(e){
            case "day":
                title_livedraw = "공주의 날"
                tab_day = "bg-[#74aa63]"
                tab_night = ""
                panel_day = true
                panel_night = false
                break;
            case "night":
                title_livedraw = "공주의 밤"
                tab_day = ""
                tab_night = "bg-[#74aa63]"
                panel_day = false
                panel_night = true
                break;
        }
    };
  </script>
<section class="hidden lg:flex gap-2 my-5">
    <Carousel />
</section>
<section class="flex w-full gap-1">
    <div class="card w-1/2 bg-base-300 shadow-xl text-neutral-content rounded-md p-2">
        <div class="card-body p-1 mb-1">
            <center class="border-b-2 border-primary-focus p-2 font-bold w-full">
                {livedraw_text_1}<br />
                {livedraw_text_2}<br />
                {livedraw_text_3} : {date_draw}
            </center>
            <div class="flex gap-1">
                <div class="text-2xl font-bold self-center ">13:00</div>
                <div class="flex justify-center gap-1 w-full ">
                    <img width="40" src="{day_img_1_prize1300}" alt="">
                    <img width="40" src="{day_img_2_prize1300}" alt="">
                    <img width="40" src="{day_img_3_prize1300}" alt="">
                    <img width="40" src="{day_img_4_prize1300}" alt="">
                    <img width="40" src="{day_img_5_prize1300}" alt="">
                    <img width="40" src="{day_img_6_prize1300}" alt="">
                </div>
            </div>
            <div class="flex gap-1">
                <div class="text-2xl font-bold self-center ">17:00</div>
                <div class="flex justify-center gap-1 w-full ">
                    <img width="40" src="{day_img_1_prize1700}" alt="">
                    <img width="40" src="{day_img_2_prize1700}" alt="">
                    <img width="40" src="{day_img_3_prize1700}" alt="">
                    <img width="40" src="{day_img_4_prize1700}" alt="">
                    <img width="40" src="{day_img_5_prize1700}" alt="">
                    <img width="40" src="{day_img_6_prize1700}" alt="">
                </div>
            </div>
            <div class="flex gap-1">
                <div class="text-2xl font-bold self-center ">20:00</div>
                <div class="flex justify-center gap-1 w-full ">
                    <img width="40" src="{day_img_1_prize2000}" alt="">
                    <img width="40" src="{day_img_2_prize2000}" alt="">
                    <img width="40" src="{day_img_3_prize2000}" alt="">
                    <img width="40" src="{day_img_4_prize2000}" alt="">
                    <img width="40" src="{day_img_5_prize2000}" alt="">
                    <img width="40" src="{day_img_6_prize2000}" alt="">
                </div>
            </div>
            <div class="flex gap-1">
                <div class="text-2xl font-bold self-center ">22:00</div>
                <div class="flex justify-center gap-1 w-full ">
                    <img width="40" src="{day_img_1_prize2200}" alt="">
                    <img width="40" src="{day_img_2_prize2200}" alt="">
                    <img width="40" src="{day_img_3_prize2200}" alt="">
                    <img width="40" src="{day_img_4_prize2200}" alt="">
                    <img width="40" src="{day_img_5_prize2200}" alt="">
                    <img width="40" src="{day_img_6_prize2200}" alt="">
                </div>
            </div>
        </div>
    </div>
    <div class="card w-full bg-base-300 shadow-xl text-neutral-content rounded-md p-2">
        <div class="card-body p-1 mb-1">
            <table class="table table-compact w-full">
                <thead>
                    <tr>
                        <th class="text-xs lg:text-lg text-center">{livedraw_text_4}</th>
                        <th class="text-xs lg:text-lg text-center">13:00</th>
                        <th class="text-xs lg:text-lg text-center">17:00</th>
                        <th class="text-xs lg:text-lg text-center">20:00</th>
                        <th class="text-xs lg:text-lg text-center">22:00</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td class="text-xs lg:text-sm text-center">2023-01-01</td>
                        <td class="text-xs lg:text-sm text-center">123456</td>
                        <td class="text-xs lg:text-sm text-center"></td>
                        <td class="text-xs lg:text-sm text-center"></td>
                        <td class="text-xs lg:text-sm text-center"></td>
                    </tr>
                    <tr>
                        <td class="text-xs lg:text-sm text-center">2023-01-01</td>
                        <td class="text-xs lg:text-sm text-center">123456</td>
                        <td class="text-xs lg:text-sm text-center">123456</td>
                        <td class="text-xs lg:text-sm text-center">123456</td>
                        <td class="text-xs lg:text-sm text-center">123456</td>
                    </tr>
                    <tr>
                        <td class="text-xs lg:text-sm text-center">2023-01-01</td>
                        <td class="text-xs lg:text-sm text-center">123456</td>
                        <td class="text-xs lg:text-sm text-center">123456</td>
                        <td class="text-xs lg:text-sm text-center">123456</td>
                        <td class="text-xs lg:text-sm text-center">123456</td>
                    </tr>
                    <tr>
                        <td class="text-xs lg:text-sm text-center">2023-01-01</td>
                        <td class="text-xs lg:text-sm text-center">123456</td>
                        <td class="text-xs lg:text-sm text-center">123456</td>
                        <td class="text-xs lg:text-sm text-center">123456</td>
                        <td class="text-xs lg:text-sm text-center">123456</td>
                    </tr>
                    <tr>
                        <td class="text-xs lg:text-sm text-center">2023-01-01</td>
                        <td class="text-xs lg:text-sm text-center">123456</td>
                        <td class="text-xs lg:text-sm text-center">123456</td>
                        <td class="text-xs lg:text-sm text-center">123456</td>
                        <td class="text-xs lg:text-sm text-center">123456</td>
                    </tr>
                    <tr>
                        <td class="text-xs lg:text-sm text-center">2023-01-01</td>
                        <td class="text-xs lg:text-sm text-center">123456</td>
                        <td class="text-xs lg:text-sm text-center">123456</td>
                        <td class="text-xs lg:text-sm text-center">123456</td>
                        <td class="text-xs lg:text-sm text-center">123456</td>
                    </tr>
                    <tr>
                        <td class="text-xs lg:text-sm text-center">2023-01-01</td>
                        <td class="text-xs lg:text-sm text-center">123456</td>
                        <td class="text-xs lg:text-sm text-center">123456</td>
                        <td class="text-xs lg:text-sm text-center">123456</td>
                        <td class="text-xs lg:text-sm text-center">123456</td>
                    </tr>
                </tbody>
            </table>
        </div>
    </div>
    
</section>
<section class="mt-5">
    <div class="flex flex-col w-full items-stretch">
        <div class="self-center">{livedraw_text_5}</div>
        <div class="flex gap-1 self-center">
            <img width="" src="visa.svg" alt="">
            <img width="" src="mastercard.svg" alt="">
            <img width="" src="paypal.svg" alt="">
        </div>
    </div>
    <div class="flex justify-between w-full mt-5">
        <p class="w-1/2 ">
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
      
        <div class="w-1/2 ">
            <center>
                <img class="place-content-center" src="google-play.png" alt="">
            </center>
        </div>
    </div>
</section>
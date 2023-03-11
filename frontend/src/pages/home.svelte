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
    const sdsb4dday = ref(db, "sdsb4dday");
    const sdsb4dnight = ref(db, "sdsb4dnight");
    
    
  
    let day_year_draw = "";
    let day_month_draw = "";
    let day_day_draw = "";
    let day_next_all = "";
    let day_next_year = "";
    let day_next_month = "";
    let day_next_day = "";
    let day_prize1 = "";
    let day_prize2 = "";
    let day_prize3 = "";
    let day_1_prize1 = "0";
    let day_2_prize1 = "0";
    let day_3_prize1 = "0";
    let day_4_prize1 = "0";

    let day_img_1_prize1 = "images/bungapink-blank.png";
    let day_img_2_prize1 = "images/bungapeach-blank.png";
    let day_img_3_prize1 = "images/bungahijau-blank.png";
    let day_img_4_prize1 = "images/bungaungu-blank.png";
    let day_img_1_prize2 = "images/bolakecilbiru-blank.png";
    let day_img_2_prize2 = "images/bolakecilpink-blank.png";
    let day_img_3_prize2 = "images/bolakecilmerah-blank.png";
    let day_img_4_prize2 = "images/bolakecilungu-blank.png";
    let day_img_1_prize3 = "images/bolakecilbiru-blank.png";
    let day_img_2_prize3 = "images/bolakecilpink-blank.png";
    let day_img_3_prize3 = "images/bolakecilmerah-blank.png";
    let day_img_4_prize3 = "images/bolakecilungu-blank.png";
    let night_date_draw = "";
    let night_year_draw = "";
    let night_month_draw = "";
    let night_day_draw = "";
    let night_next_draw = "";
    let night_next_year = "";
    let night_next_month = "";
    let night_next_day = "";
    let night_prize1 = "";
    let night_prize2 = "";
    let night_prize3 = "";
    let night_img_1_prize1 = "number/ball-null.png";
    let night_img_2_prize1 = "number/ball-null.png";
    let night_img_3_prize1 = "number/ball-null.png";
    let night_img_4_prize1 = "number/ball-null.png";
    let night_img_1_prize2 = "number/ball-null.png";
    let night_img_2_prize2 = "number/ball-null.png";
    let night_img_3_prize2 = "number/ball-null.png";
    let night_img_4_prize2 = "number/ball-null.png";
    let night_img_1_prize3 = "number/ball-null.png";
    let night_img_2_prize3 = "number/ball-null.png";
    let night_img_3_prize3 = "number/ball-null.png";
    let night_img_4_prize3 = "number/ball-null.png";
    let temp_day = "";
    let temp_day_hour = "00";
    let temp_day_minute = "00";
    let temp_day_second = "00";
    onValue(sdsb4dday, (snapshot) => {
        const data = snapshot.val();
        day_year_draw = dayjs(data["datedraw"]).format("YYYY");;
        day_month_draw = dayjs(data["datedraw"]).format("MM");;
        day_day_draw = dayjs(data["datedraw"]).format("DD");;
        day_next_year = dayjs(data["nextdraw"]).format("YYYY");
        day_next_month = dayjs(data["nextdraw"]).format("MM");
        day_next_day = dayjs(data["nextdraw"]).format("DD");
        day_next_all = dayjs(data["nextdraw"]).format("YYYY년 MM월 DD일");
        day_prize1 = data["prize1"];
        day_prize2 = data["prize2"];
        day_prize3 = data["prize3"];
        day_1_prize1 = day_prize1[0];
        day_2_prize1 = day_prize1[1];
        day_3_prize1 = day_prize1[2];
        day_4_prize1 = day_prize1[3];
        day_img_1_prize1 = getImage(day_prize1[0],"bungapink");
        day_img_2_prize1 = getImage(day_prize1[1],"bungapeach");
        day_img_3_prize1 = getImage(day_prize1[2],"bungahijau");
        day_img_4_prize1 = getImage(day_prize1[3],"bungaungu");
        day_img_1_prize2 = getImage(day_prize2[0],"bolakecilbiru");
        day_img_2_prize2 = getImage(day_prize2[1],"bolakecilpink");
        day_img_3_prize2 = getImage(day_prize2[2],"bolakecilmerah");
        day_img_4_prize2 = getImage(day_prize2[3],"bolakecilungu");
        day_img_1_prize3 = getImage(day_prize3[0],"bolakecilbiru");
        day_img_2_prize3 = getImage(day_prize3[1],"bolakecilpink");
        day_img_3_prize3 = getImage(day_prize3[2],"bolakecilmerah");
        day_img_4_prize3 = getImage(day_prize3[3],"bolakecilungu");
        temp_day = dayjs(data["nextdraw"] + " 15:00:00").valueOf();
        setInterval(function () {
            let now = new Date().getTime();
            let distance = temp_day - now;
            let hours = Math.floor(
                (distance % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60)
            );
            let minutes = Math.floor(
                (distance % (1000 * 60 * 60)) / (1000 * 60)
            );
            let seconds = Math.floor((distance % (1000 * 60)) / 1000);
            temp_day_hour = hours;
            temp_day_minute = minutes;
            temp_day_second = seconds;
            if (hours < 10) {
                temp_day_hour = "0" + hours;
            } else {
                temp_day_hour = hours;
            }
            if (minutes < 10) {
                temp_day_minute = "0" + minutes;
            } else {
                temp_day_minute = minutes;
            }
            if (seconds < 10) {
                temp_day_second = "0" + seconds;
            } else {
                temp_day_second = seconds;
            }
            if (distance < 0) {
                clearInterval();
                temp_day_hour = "00";
                temp_day_minute = "00";
                temp_day_second = "00";
            }
            
        }, 1000);
    });
    let temp_night = "";
    let temp_night_hour = "00";
    let temp_night_minute = "00";
    let temp_night_second = "00";
    let tab_day = "bg-[#74aa63]"
    let tab_night = ""
    let panel_day = true
    let panel_night = false

    
    onValue(sdsb4dnight, (snapshot) => {
        const data = snapshot.val();
        night_date_draw = data["datedraw"];
        night_year_draw = dayjs(data["datedraw"]).format("YYYY");
        night_month_draw = dayjs(data["datedraw"]).format("MM");
        night_day_draw = dayjs(data["datedraw"]).format("DD");
        night_next_draw = dayjs(data["nextdraw"]).format("YYYY년 MM월 DD일");
        night_next_year = dayjs(data["nextdraw"]).format("YYYY");
        night_next_month = dayjs(data["nextdraw"]).format("MM");
        night_next_day = dayjs(data["nextdraw"]).format("DD");
        night_prize1 = data["prize1"];
        night_prize2 = data["prize2"];
        night_prize3 = data["prize3"];
        night_img_1_prize1 = getImage(night_prize1[0],"bungapink");
        night_img_2_prize1 = getImage(night_prize1[1],"bungapeach");
        night_img_3_prize1 = getImage(night_prize1[2],"bungahijau");
        night_img_4_prize1 = getImage(night_prize1[3],"bungaungu");
        night_img_1_prize2 = getImage(night_prize2[0],"bolakecilbiru");
        night_img_2_prize2 = getImage(night_prize2[1],"bolakecilpink");
        night_img_3_prize2 = getImage(night_prize2[2],"bolakecilmerah");
        night_img_4_prize2 = getImage(night_prize2[3],"bolakecilungu");
        night_img_1_prize3 = getImage(night_prize3[0],"bolakecilbiru");
        night_img_2_prize3 = getImage(night_prize3[1],"bolakecilpink");
        night_img_3_prize3 = getImage(night_prize3[2],"bolakecilmerah");
        night_img_4_prize3 = getImage(night_prize3[3],"bolakecilungu");
        temp_night = dayjs(data["nextdraw"] + " 21:00:00").valueOf();
        setInterval(function () {
            let now = new Date().getTime();
            let distance = temp_night - now;
            let hours = Math.floor(
                (distance % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60)
            );
            let minutes = Math.floor(
                (distance % (1000 * 60 * 60)) / (1000 * 60)
            );
            let seconds = Math.floor((distance % (1000 * 60)) / 1000);
            if (hours < 10) {
                temp_night_hour = "0" + hours;
            } else {
                temp_night_hour = hours;
            }
            if (minutes < 10) {
                temp_night_minute = "0" + minutes;
            } else {
                temp_night_minute = minutes;
            }
            if (seconds < 10) {
                temp_night_second = "0" + seconds;
            } else {
                temp_night_second = seconds;
            }
            if (distance < 0) {
                clearInterval();
                temp_night_hour = "00";
                temp_night_minute = "00";
                temp_night_second = "00";
            }
        }, 1000);
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
                WINNING NUMBER<br />
                6D RESULT<br />
                DRAW : March 11, 2023
            </center>
            <div class="flex gap-1">
                <div class="text-2xl font-bold self-center ">13:00</div>
                <div class="flex justify-center gap-1 w-full ">
                    <img width="40" src="images/ball-0.png" alt="">
                    <img width="40" src="images/ball-1.png" alt="">
                    <img width="40" src="images/ball-2.png" alt="">
                    <img width="40" src="images/ball-3.png" alt="">
                    <img width="40" src="images/ball-4.png" alt="">
                    <img width="40" src="images/ball-5.png" alt="">
                </div>
            </div>
            <div class="flex gap-1">
                <div class="text-2xl font-bold self-center ">17:00</div>
                <div class="flex justify-center gap-1 w-full ">
                    <img width="40" src="images/ball-0.png" alt="">
                    <img width="40" src="images/ball-1.png" alt="">
                    <img width="40" src="images/ball-2.png" alt="">
                    <img width="40" src="images/ball-3.png" alt="">
                    <img width="40" src="images/ball-4.png" alt="">
                    <img width="40" src="images/ball-5.png" alt="">
                </div>
            </div>
            <div class="flex gap-1">
                <div class="text-2xl font-bold self-center ">20:00</div>
                <div class="flex justify-center gap-1 w-full ">
                    <img width="40" src="images/ball-null.png" alt="">
                    <img width="40" src="images/ball-null.png" alt="">
                    <img width="40" src="images/ball-null.png" alt="">
                    <img width="40" src="images/ball-null.png" alt="">
                    <img width="40" src="images/ball-null.png" alt="">
                    <img width="40" src="images/ball-null.png" alt="">
                </div>
            </div>
            <div class="flex gap-1">
                <div class="text-2xl font-bold self-center ">22:00</div>
                <div class="flex justify-center gap-1 w-full ">
                    <img width="40" src="images/ball-null.png" alt="">
                    <img width="40" src="images/ball-null.png" alt="">
                    <img width="40" src="images/ball-null.png" alt="">
                    <img width="40" src="images/ball-null.png" alt="">
                    <img width="40" src="images/ball-null.png" alt="">
                    <img width="40" src="images/ball-null.png" alt="">
                </div>
            </div>
        </div>
    </div>
    <div class="card w-full bg-base-300 shadow-xl text-neutral-content rounded-md p-2">
        <div class="card-body p-1 mb-1">
            <table class="table table-compact w-full">
                <thead>
                    <tr>
                        <th class="text-xs lg:text-lg text-center">DATE</th>
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
        <div class="self-center">We accept these payment method</div>
        <div class="flex gap-1 self-center">
            <img width="" src="visa.svg" alt="">
            <img width="" src="mastercard.svg" alt="">
            <img width="" src="paypal.svg" alt="">
        </div>
    </div>
    <div class="flex justify-between w-full mt-5">
        <p class="w-full ">
            Players must be 18 years old. If you do not have control, gambling may be harmful. Please, play with responsibility.
            All efforts will be made to ensure accuracy of the prizes, winnings and other information posted on hanoilottery.com. 
            Official Winning Numbers are those that are selected in the respective drawings and are controlled by an independent accounting firm.
            In case of non-compliance, official winning results will prevail.
            The "Hanoi" trademark registration number 958786573-gf-94515 is owned and operated by the Lotera Association of Hanoi Lotera.
            <br>
            <br>
            Người chơi phải đủ 18 tuổi. Nếu bạn không kiểm soát, cờ bạc có thể gây hại. Xin vui lòng, chơi với trách nhiệm.
Mọi nỗ lực sẽ được thực hiện để đảm bảo tính chính xác của giải thưởng, tiền thắng cược và các thông tin khác được đăng trên hanoilottery.com.
Số trúng thưởng chính thức là những số được chọn trong các bản vẽ tương ứng và được kiểm soát bởi một công ty kế toán độc lập.
Trong trường hợp không tuân thủ, kết quả chiến thắng chính thức sẽ được áp dụng.
Số đăng ký nhãn hiệu "Hà Nội" 958786573-gf-94515 được sở hữu và điều hành bởi Hiệp hội Lotera Hà Nội Lotera.
        </p>
      
        <div class="w-1/2 ">
            <center>
                <img class="place-content-center" src="google-play.png" alt="">
            </center>
        </div>
    </div>
</section>

flowchart LR

    Driver["راننده"]
    Manager["مدیر پارکینگ"]
    Operator["اپراتور پارکینگ"]
    Reviewer["مسئول بررسی و تأیید"]
    Admin["مدیر سیستم"]
    Gateway["درگاه پرداخت"]

    subgraph System["سامانه هوشمند مدیریت پارکینگ‌های شهری"]

        subgraph DriverServices["خدمات راننده"]
            D1(["ثبت‌نام و ورود"])
            D2(["جست‌وجوی پارکینگ"])
            D3(["مشاهده اطلاعات پارکینگ"])
            D4(["مشاهده ظرفیت خالی"])
            D5(["رزرو جای پارک"])
            D6(["لغو رزرو"])
            D7(["محاسبه هزینه تقریبی"])
            D8(["پرداخت هزینه"])
            D9(["دریافت رسید"])
        end

        subgraph ManagerServices["مدیریت پارکینگ"]
            M1(["ثبت پارکینگ جدید"])
            M2(["ثبت اطلاعات پارکینگ"])
            M3(["ارسال درخواست ثبت"])
            M4(["پیگیری وضعیت درخواست"])
            M5(["اصلاح اطلاعات پارکینگ"])
            M6(["مدیریت اطلاعات پارکینگ"])
            M7(["مدیریت ظرفیت و تعرفه"])
            M8(["مدیریت رزروها"])
            M9(["تخصیص اپراتور"])
            M10(["مشاهده گزارش پارکینگ"])
        end

        subgraph OperatorServices["عملیات اپراتور"]
            O1(["مشاهده و بررسی رزروها"])
            O2(["تأیید یا رد ورود راننده"])
            O3(["ثبت ورود خودرو"])
            O4(["ثبت خروج خودرو"])
            O5(["محاسبه هزینه نهایی"])
            O6(["به‌روزرسانی ظرفیت"])
            O7(["ثبت فعالیت روزانه"])
            O8(["مشاهده سوابق پارکینگ"])
        end

        subgraph ReviewServices["بررسی و تأیید پارکینگ"]
            R1(["مشاهده درخواست‌ها"])
            R2(["بررسی اطلاعات پارکینگ"])
            R3(["تأیید درخواست"])
            R4(["رد درخواست"])
            R5(["بازگرداندن برای اصلاح"])
            R6(["فعال‌سازی پارکینگ"])
        end

        subgraph AdminServices["مدیریت کل سامانه"]
            A1(["مدیریت کاربران"])
            A2(["مدیریت نقش‌ها و دسترسی‌ها"])
            A3(["مدیریت همه پارکینگ‌ها"])
            A4(["مدیریت اپراتورها"])
            A5(["گزارش‌های کل سامانه"])
            A6(["سوابق فعالیت سیستم"])
        end

        subgraph PaymentServices["پرداخت"]
            P1(["پردازش تراکنش"])
            P2(["اعلام نتیجه پرداخت"])
        end
    end

    Driver --> D1
    Driver --> D2
    Driver --> D5
    Driver --> D6
    Driver --> D7
    Driver --> D8
    Driver --> D9

    D2 -.->|شامل| D3
    D3 -.->|شامل| D4
    D5 -.->|شامل| D4
    D8 -.->|شامل| P1
    D8 -.->|شامل| D9

    Manager --> M1
    Manager --> M4
    Manager --> M5
    Manager --> M6
    Manager --> M7
    Manager --> M8
    Manager --> M9
    Manager --> M10

    M1 -.->|شامل| M2
    M1 -.->|شامل| M3
    M5 -.->|شامل| M2

    Operator --> O1
    Operator --> O2
    Operator --> O3
    Operator --> O4
    Operator --> O7
    Operator --> O8

    O3 -.->|شامل| O6
    O4 -.->|شامل| O5
    O4 -.->|شامل| O6

    Reviewer --> R1
    Reviewer --> R2
    Reviewer --> R3
    Reviewer --> R4
    Reviewer --> R5

    R2 -.->|شامل| R1
    R3 -.->|شامل| R6

    Admin --> A1
    Admin --> A2
    Admin --> A3
    Admin --> A4
    Admin --> A5
    Admin --> A6

    Gateway --> P1
    Gateway --> P2
    P1 -.->|شامل| P2

    N1["هر مدیر می‌تواند چندین پارکینگ را مدیریت کند."]
    N2["هر پارکینگ دارای ظرفیت، تعرفه و اپراتور مستقل است."]
    N3["هر اپراتور فقط به پارکینگ تخصیص‌یافته دسترسی دارد."]

    M6 --- N1
    M7 --- N2
    O8 --- N3

    style System fill:#F8FAFC,stroke:#1E3A8A,stroke-width:3px
    style DriverServices fill:#EFF6FF,stroke:#2563EB
    style ManagerServices fill:#F0FDF4,stroke:#16A34A
    style OperatorServices fill:#FFF7ED,stroke:#EA580C
    style ReviewServices fill:#FAF5FF,stroke:#9333EA
    style AdminServices fill:#FDF2F8,stroke:#DB2777
    style PaymentServices fill:#FEFCE8,stroke:#CA8A04

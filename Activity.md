flowchart TD
    START(("شروع")) --> A["ورود راننده به سامانه"]
    A --> B["جست‌وجوی پارکینگ"]
    B --> C["انتخاب پارکینگ و زمان"]
    C --> D["ثبت اطلاعات رزرو"]
    D --> E{"اطلاعات معتبر است؟"}

    E -->|خیر| F["نمایش خطا"]
    F --> D

    E -->|بله| G{"ظرفیت موجود است؟"}
    G -->|خیر| H["اعلام تکمیل ظرفیت"]
    H --> END(("پایان"))

    G -->|بله| I["محاسبه هزینه"]
    I --> J["پرداخت هزینه"]
    J --> K{"پرداخت موفق است؟"}

    K -->|خیر| L["لغو رزرو موقت"]
    L --> END

    K -->|بله| M["ثبت نهایی رزرو"]
    M --> N["تولید کد پیگیری"]
    N --> O["به‌روزرسانی ظرفیت پارکینگ"]
    O --> P["نمایش رسید رزرو"]
    P --> END

    classDef startEnd fill:#17365D,color:#FFFFFF,stroke:#10243A,stroke-width:2px;
    classDef action fill:#EAF2F8,color:#17365D,stroke:#4472C4;
    classDef decision fill:#FFF2CC,color:#7F6000,stroke:#BF9000;
    classDef error fill:#FCE4D6,color:#9C0006,stroke:#C00000;
    classDef success fill:#E2F0D9,color:#375623,stroke:#70AD47;

    class START,END startEnd;
    class A,B,C,D,I,J,M,N,O,P action;
    class E,G,K decision;
    class F,H,L error;
    class M,N,O,P success;

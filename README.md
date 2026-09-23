# Laragon-Database-Import

Laragon Terminal ব্যবহার করে সহজে ও দ্রুত `.sql` ডাটাবেজ ইমপোর্ট করার সহজ গাইডলাইন।

---

### **পদ্ধতি ১: সাধারণ টার্মিনাল থেকে সরাসরি ইমপোর্ট (সবচেয়ে সহজ)**

Laragon-এর **Terminal** ওপেন করে সরাসরি নিচের কমান্ডটি রান করুন:

#### ১. ডাটাবেজ তৈরি করা না থাকলে:
```bash
mysql -u root -p -e "CREATE DATABASE database_name;"
```

#### ২. সরাসরি ডাটাবেজ ইমপোর্ট করা:
```bash
mysql -u root -p database_name < "C:/path/to/your_file.sql"
```

> **বাস্তব উদাহরণ:**
> ```bash
> mysql -u root -p spz < "C:/Users/Md Ashikur Rahman/Downloads/spzbd_soft_export.sql"
> ```
> *(পাসওয়ার্ড চাইলে পাসওয়ার্ড দিন, আর ডিফল্ট ফাঁকা থাকলে সরাসরি `Enter` চাপুন)*

---

### **পদ্ধতি ২: MySQL শেলের ভেতরে থাকলে (`source` কমান্ড দিয়ে)**

আপনি যদি ইতোমধ্যে `mysql -u root -p` দিয়ে ভেতরে ঢুকে থাকেন (`mysql>` দেখতে পান):

#### ১. ডাটাবেজ সিলেক্ট করুন:
```sql
USE spz;
```

#### ২. ফাইল ইমপোর্ট করুন:
```sql
source C:/Users/Md Ashikur Rahman/Downloads/spzbd_soft_export.sql;
```

*(Note: ফাইলের পাথে ব্যাকস্ল্যাশ `\` এর বদলে ফরোয়ার্ড স্ল্যাশ `/` ব্যবহার করবেন)*

---

### **জরুরি টিপ (বড় ফাইলের জন্য):**

যদি ফাইল অনেক বড় হয় এবং `max_allowed_packet` বা `server has gone away` এরর আসে, তবে এই কমান্ডটি ব্যবহার করুন:

```bash
mysql -u root -p --max_allowed_packet=512M database_name < "C:/path/to/your_file.sql"
```

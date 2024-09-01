# استخدم صورة Node.js كأساس
FROM node:20

# تعيين مجلد العمل
WORKDIR /usr/src/app

# نسخ package.json و package-lock.json
COPY package*.json ./

# تثبيت الاعتمادات
RUN npm install

# نسخ كل الملفات
COPY . .

# بناء التطبيق
RUN npm run build

# تعيين المنفذ الذي يعمل عليه التطبيق
EXPOSE 3000

# تشغيل التطبيق
CMD ["npm", "run", "dev"]

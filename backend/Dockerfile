# استخدم صورة Node.js كأساس
FROM node:20 AS builder

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

# مرحلة الإنتاج
FROM node:20 AS production

# تعيين مجلد العمل
WORKDIR /usr/src/app

# نسخ package.json و package-lock.json
COPY package*.json ./

# تثبيت الاعتمادات لـ production فقط
RUN npm install --only=production

# نسخ الملفات من مرحلة البناء
COPY --from=builder /usr/src/app/dist ./dist

# تعيين المنفذ الذي يعمل عليه التطبيق
EXPOSE 3000

# تشغيل التطبيق في وضع الإنتاج
CMD ["npm", "run", "start:prod"]

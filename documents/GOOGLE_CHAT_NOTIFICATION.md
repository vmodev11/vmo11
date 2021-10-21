# Hướng dẫn tích hợp notification cho google chat đối với luồng CI/CD cơ bản
1. Setup google chat webhook [ở đây](https://developers.google.com/chat/how-tos/webhooks#define_an_incoming_webhook). Chỉ cần quan tâm đến giá trị webhook URL
## Gitlab
1. Xem hướng dẫn chi tiết [ở đây](https://docs.gitlab.com/ee/user/project/integrations/hangouts_chat.html)
2. Setup notification khi chạy CI/CD
  - Xem file cấu hình [ở đây](https://gist.github.com/huyhavmodev/498034b3596855802ab219736f313018)
  - Lưu ý, chỉ cần quan tấm đến file `.gitlab-ci.yml`.
  - Biến `$GOOGLE_CHAT_WEBHOOK` được cấu hình thông qua Gitlab CI/CD variable (public hay protected tùy thuộc vào mục đích triển khai). 
Xem hướng dẫn ở phần 1 để biết giá trị của biến này
# Github
1. Xem hướng dẫn chi tiết [ở đây](https://support.google.com/chat/answer/9632291?hl=vi&co=GENIE.Platform%3DDesktop&oco=0)
2. Setup notification khi chạy CI/CD
  - Sử dụng github action đã được đóng gói [ở đây](https://github.com/marketplace/actions/google-chat-notification)
  - Biến `$GOOGLE_CHAT_WEBHOOK` được cấu hình thông qua Github environment secrets. 
Xem hướng dẫn ở phần 1 để biết giá trị của biến này

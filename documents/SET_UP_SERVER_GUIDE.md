## Checklist for setup server

- [ ] Note: **Always use strong password**
- [ ] Install nginx
- [ ] Install mongoDB
- [ ] Install AWS cli
- [ ] Install docker
- [ ] Enable service: nginx, mongod, docker
- [ ] Config mongo user and enable remote
  - [ ] Access mongo => createUser admin with roles is root
  - [ ] Edit /etc/mongod.conf => change IP to 0.0.0.0 => **enable secure authentication** (required)
  - [ ] Restart mongo service
  - [ ] Access mongo with admin user
  - [ ] Create DB => create db user with roles is readAndWrite
- [ ] Config nginx
- [ ] Install certbot and setup cert

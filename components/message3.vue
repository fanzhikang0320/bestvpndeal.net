<template>
  <div class="alert-wrapper">
      <div class="alert-content">
          <span class="close" @click="closeAlert"></span>
          <div class="link-box">
              <div class="box-top">
                  <div class="box-top-left">
                      <img src="/data/img/NordVPN.png" alt="NordVPN" class="logo">
                  </div>
                  <div class="box-top-right">
                      <h1 class="text">Final Sale: <span class="red">68%</span> Off</h1>
                      <p class="desc">Best VPN of 2021</p>
                  </div>
              </div>
              <div class="box-bottom">
                  <div class="info-box">
                      <img src="@/assets/image/message3.png" alt="NordVPN" class="pic">
                      <ul class="list">
                          <li>
                              <span class="icon m1"></span>
                              <p class="text">Securely Stream TV Shows</p>
                          </li>
                          <li>
                              <span class="icon m2"></span>
                              <p class="text">Strict No-Logs Policy</p>
                          </li>
                          <li>
                              <span class="icon m3"></span>
                              <p class="text">Blazing Speeds</p>
                          </li>
                          <li>
                              <span class="icon m4"></span>
                              <p class="text">Automatic Kill Switch</p>
                          </li>
                      </ul>
                  </div>
                  <a href="https://go.nordvpn.net/aff_c?offer_id=328&aff_id=48575&source=popup" target="_blank" class="btn" rel="noopener noreferrer nofollow">Save Now</a>
                  <dl class="device-list">
                      <dt>Availble:</dt>
                      <dd>
                          <img src="@/assets/image/android.svg" alt="android" class="pic">
                      </dd>
                      <dd>
                          <img src="@/assets/image/macOS.svg" alt="macOS" class="pic">
                      </dd>
                      <dd>
                          <img src="@/assets/image/iOS.svg" alt="iOS" class="pic">
                      </dd>
                      <dd>
                          <img src="@/assets/image/router.svg" alt="router" class="pic">
                      </dd>
                      <dd>
                          <img src="@/assets/image/linux.svg" alt="linux" class="pic">
                      </dd>
                      <dd>
                          <img src="@/assets/image/windows.svg" alt="windows" class="pic">
                      </dd>
                      <dd>
                          <img src="@/assets/image/chrome.svg" alt="chrome" class="pic">
                      </dd>
                      <dd>
                          <img src="@/assets/image/firefox.svg" alt="firefox" class="pic">
                      </dd>
                      <dd>
                          <img src="@/assets/image/gameConsole.svg" alt="GameConsole" class="pic">
                      </dd>
                      <dd>
                          <img src="@/assets/image/smartTV.svg" alt="smartTV" class="pic">
                      </dd>
                  </dl>
              </div>
          </div>
      </div>
  </div>
</template>

<script>
export default {
    
    props: ['url'],
    data: () => {
        return {
            timer: null,
            timer2: null,
            count: 0
        }
    },
    methods: {
        showAlert() {
                $('.alert-wrapper').css({
                    display: 'block'
                    
                }).animate({
                    opacity: 1
                },200)
                $('.alert-content').animate({
                    top: '50%',
                    opacity: 1
                },400)
        },
        closeAlert() {
            this.$nextTick(() => {
                $('.alert-content').animate({
                    top: '40%',
                    opacity: 0
                },400,function () {
                    
                })
                $('.alert-wrapper').animate({
                    opacity: 0
                },500,function () {
                    $(this).css({
                        display: 'none'
                    })
                })
                
                
            })
        }
    },
    mounted() {
        $('body').on('click',() => {
            this.closeAlert();
        })
        this.timer2 = setTimeout(() => {
            $('body').on('mouseenter',() => {
                $('body').one('mouseleave',() => {
                    if (this.count == 0) {
                        this.showAlert();
                    }
                    this.count ++;
                })
            })
        },25000)
        
    },
    destroyed() {
        clearInterval(this.timer);
        clearTimeout(this.timer2)
    }
}
</script>
<style lang="scss" scoped>
.alert-wrapper {
    position: fixed;
    top: 0;
    left: 0;
    z-index: 999;
    width: 100%;
    height: 100%;
    background-color: rgba(0,0,0,.55);
    display:none;
    opacity: 0;
    .alert-content {
        width: 800px;
        height: 500px;
        position: absolute;
        left: 50%;
        top: 30%;
        transform: translate(-50%,-50%);
        
        opacity: 0;
        .close {
            position: absolute;
            top: -30px;
            right: -30px;
            width: 30px;
            height: 30px;
            cursor: pointer;
            z-index: 1;
            &::after, &::before {
                content: '';
                position: absolute;
                left: 50%;
                top: 50%;
                width: 30px;
                height: 4px;
                background-color: rgb(155,157,198);
            }

            &::after {
                transform: translate(-50%,-50%) rotateZ(-45deg);
            }
            &::before {
                transform: translate(-50%,-50%) rotateZ(45deg);
            }
            
        }
        .link-box {
            width: 100%;
            height: 100%;

            .box-top {
                display: flex;
                align-items: center;
                height: 170px;
                width: 100%;

                .box-top-left {
                    position: relative;
                    display: inline-block;
                    height: 100%;
                    width: 340px;
                    background-color: #a8dae3;

                    &::after {
                        content: '';
                        position: absolute;
                        right: 0;
                        top: 0;
                        width: 0;
                        height: 0;

                        border-top: 85px solid #274f94;
                        border-bottom: 85px solid transparent;
                        border-right: 50px solid #274f94;
                        border-left: 50px solid transparent;

                    }

                    .logo {
                        position: absolute;
                        left: 65px;
                        top: 10px;
                        width: 140px;
                    }


                }
                .box-top-right {
                    display: inline-block;
                    width: 460px;
                    height: 100%;
                    background-color: #274f94;
                    text-align: center;
                    .text {
                        font-size: 43px;
                        color: #fff;
                        margin-top: 45px;
                        .red {
                            color: #ff4b2d;
                        }
                    }
                    .desc {
                        text-align: center;
                        font-size: 35px;
                        color: #ff4b2d;
                        font-weight: 700;
                    }
                }
            }
            .box-bottom {
                height: 330px;
                box-sizing: border-box;
                background-color: #fff;
                display: flex;
                flex-direction: column;
                align-items: center;
                .info-box {
                    display: flex;
                    align-items: center;
                    justify-content: center;
                    margin-top: 26px;
                    .pic {
                        width: 300px;
                        margin-right: 70px;
                    }
                        .list {
                            
                            
                            li {
                                display: flex;
                                align-items: center;
                                margin-bottom: 10px;
                                .icon {
                                    display: inline-block;
                                    width: 18px;
                                    height: 18px;
                                    margin-right: 10px;
                                    
                                    background-repeat: no-repeat;
                                    background-size: cover;
                                    background-position: center center;

                                    &.m1 {
                                        background-image: url('../assets/image/m-icon-1.png');
                                    }
                                    &.m2 {
                                        background-image: url('../assets/image/m-icon-2.png');
                                    }
                                    &.m3 {
                                        background-image: url('../assets/image/m-icon-3.png');
                                    }
                                    &.m4 {
                                        background-image: url('../assets/image/m-icon-4.png');
                                    }
                                }
                                .text {
                                    font-size: 20px;
                                }
                            }
                        }
                }

                .btn {
                    display: inline-block;
                    width: 300px;
                    height: 60px;
                    margin-top: 8px;
                    margin-bottom: 20px;
                    color: #ffff;
                    font-size: 25px;
                    line-height: 60px;
                    text-align: center;
                    text-decoration: none;
                    border-radius: 8px;
                    font-weight: 700;
                    background-color: #ff4b2d;
                    box-shadow: 4px 10px 13px 0px rgba(0, 0, 0, 0.6);
                    transition: all linear 0.1s;
                    &:hover {
                        box-shadow: 2px 7px 10px 0px rgba(0, 0, 0, 0.3);
                    }
                }

                .device-list {
                    display: flex;
                    align-items: center;
                    img {
                        width: 18px;
                        height: 18px;
                        margin-left: 13px;
                    }
                }
            }
        }
        
    }
}
</style>
<template>
    <div class="ui-header">
        <div data-topbar="true" class="contain-to-grid sticky">
            <nav class="top-bar">
                <section class="top-bar-section">
                    <ul class="right">
                        <li class="active"><a href="/">دروس الطباعة</a></li>
                        <li><a href="/about">اختبار السرعة</a></li>
                        <li><a href="/training">نصوص للتدرب</a></li>
                    </ul>
                    <div>
                        <!---->
                        <ul class="left">
                            <li>
                                <div><button @click='showRegisteratoin=!showRegisteratoin' class="login">تسجيل /
                                        دخول</button>
                                   
                                </div>
                            </li>
                        </ul>
                        
                    </div>
                </section>
            </nav>
        </div>
    </div>

    <!-- لوحة تسجيل الدخول -->
    <div v-if="showRegisteratoin">

        <div class="tb-dialog-container">
            <div class="tb-dialog-header">
                <div> <a href="#" class="pull-left"><i class="fa fa-times"></i></a>
                </div>
            </div>
            <div class="tb-dialog-body">
                <div>
                    <div class="row login-container">
                        <div class="login-or hide-for-small-only"><span
                                class="or">أو</span></div>
                        <!---->
                        <div class="column medium-6 login-column">
                            <h3><span>إنشاء حساب جديد</span></h3>
                            <form class="log-in-form"><input autocomplete="none"
                                    name="hidden" type="text" style="display: none;">
                                <label>اسم الدخول
                                    <input type="text" name="username"
                                        autocomplete="off" autocorrect="off"
                                        autocapitalize="none" spellcheck="false">
                                    <p class="error-msg" style="display: none;">رجاءا
                                        أدخل اسم الدخول</p>
                                    <p class="error-msg" style="display: none;">
                                        اسم الدخول غير صحيح.
                                        <br>
                                        قواعد اسم الدخول:
                                        <br>
                                        * أطول من 3 أحرف وأقل من 50 حرف.
                                        <br>
                                        * يتكون من أحرف أو أرقام عربية أو أجنبية.
                                    </p>
                                    <p class="error-msg" style="display: none;">اسم
                                        الدخول غير متاح</p>
                                </label> <label>البريد الالكتروني
                                    <input type="email" name="email">
                                    <p class="error-msg" style="display: none;">رجاءا
                                        أدخل البريد الالكتروني</p>
                                    <p class="error-msg" style="display: none;">البريد
                                        الالكتروني غير صحيح</p>
                                    <p class="error-msg" style="display: none;">البريد
                                        الإلكتروني موجود مسبقا</p>
                                </label> <label>كلمة السر
                                    <input type="password" name="password"
                                        autocomplete="new-password">
                                    <p class="error-msg" style="display: none;">رجاءا
                                        أدخل كلمة السر</p>
                                    <p class="error-msg" style="display: none;">كلمة
                                        السر يجب أن تتكون على الأقل 4 أحرف</p>
                                </label> <label><input type="checkbox"
                                        name="remember-me">
                                    تذكرني
                                </label>
                                <p class="error-msg" style="display: none;"></p>
                                <div><button type="submit"
                                        class="button expand success"><i
                                            class="fa fa-fw fa-spin fa-spinner"
                                            style="display: none;"></i>
                                        إنشاء حساب جديد</button></div>
                            </form>
                            
                        </div>
                        <div class="column medium-6 register-column">
                            <h3><span>تسجيل الدخول</span></h3>
                            <form class="log-in-form"><label>اسم الدخول أو الإيميل
                                    <input type="text" name="username"
                                        required="required" autocorrect="off"
                                        autocapitalize="none"
                                        spellcheck="false"></label> <label>كلمة السر
                                    <input type="password" name="password"
                                        required="required"></label> <label><input
                                        type="checkbox" name="remember-me">
                                    تذكرني
                                </label>
                                <!---->
                                <div><button type="submit" class="button expand"><i
                                            class="fa fa-fw fa-spin fa-spinner"
                                            style="display: none;"></i>
                                        تسجيل الدخول</button></div>
                              
                            </form> <br>
                        </div>
                    </div>
                </div>
            </div>
            <div class="tb-dialog-footer">
                <div></div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        data:function(){
            return{
                showRegisteratoin:false,
                
            } 


        }
    }
</script>

<style scoped>
    div.tb-dialog-container{
        font-size:.8em;
    }
</style>
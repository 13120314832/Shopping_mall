<template>
<div class="Bin_Cfn_Body" id="Bin_Cfn_Body">
    <!-- 动态加载 content -->
    <div class="Bin_Cfn_Body_Content">
        <!-- 左侧 -->
        <div class="b_r b_b Bin_Cfn_Body_Content_Left">
        <div class="">
            <p>红色</p>
        </div>
        <div class="">
            <p>蓝色</p>
        </div>
        </div>
        <!-- 右侧 -->
        <div class="Bin_Cfn_Body_Content_Right">
        <!-- 第一行 -->
        <div class="Right_Specific">
            <div><p>S</p></div> 
            <div><p>*价格</p></div> 
            <div><button class="btn_click">+添加图片</button></div> 
            <div><p>商家编码</p></div> 
            <div><p>商品条形码</p></div>
            <button class="btn_click">展开》</button>                                        
        </div>
        <!-- 第二行 -->
        <div class="Right_Stock">
            <p>库存</p>
        </div>
        <!-- 第三行 -->
        <div class="Right_Address">
            <div><p>地址</p></div>
            <div><p>数量</p></div>
            <div><p>操作</p></div>
        </div>
        <!-- 第四行 -->
        <div class="Right_Edit">
            <div>
            <input type="text">
            <span class="btn_click">编辑</span>
            </div>
            <div><p>数量</p></div>
            <div><span class="btn_click">删除</span></div>
            <button class="btn_click">+</button>                      
        </div>
        </div>
    </div>
</div>
</template>
<style scoped>

/* 具体内容 */
.Bin_Cfn_Body{
  width: 100%;
  background: #ffffff;
  border: 1px solid #cccccc;  
  border-top: none;
  height: 200px;
}
.Bin_Cfn_Body_Content{
  width: 100%;
  height: 100%;
}
.Bin_Cfn_Body_Content_Left{
  width: 135px;
  float: left;
  height: 200px;
}
.Bin_Cfn_Body_Content_Left div{
  width: 100%;
  height: 30px;
  text-align: center;
  border-bottom: 1px solid #cccccc;      
}
.Bin_Cfn_Body_Content div p{
  font-size: 12px;
  line-height: 30px;
  color: #b6b6b6;
}
.Bin_Cfn_Body_Content div span{
  font-size: 12px;
  line-height: 30px;
  text-decoration:underline;
}
.Bin_Cfn_Body_Content_Right{
  width: 679px;
  float: left;
  height: 100px;
}
.Bin_Cfn_Body_Content_Right>div{
  width: 100%;
  border-bottom: 1px solid #cccccc;      
  height: 30px;
}
.Bin_Cfn_Body_Content_Right>div>div{
  width: 135px;
  height: 30px;
  float: left;
  border-right: 1px solid #cccccc;     
}
.Bin_Cfn_Body_Content_Right>div>div:nth-child(5){
  border-right: none;    
}
.Bin_Cfn_Body_Content_Right button{
  width: 79px;
  height: 23px;
  border: 1px solid #cccccc;  
  color: #b8b8b8;
  margin: 4px 28px;  
}
.Right_Specific{
  position: relative;
}
.Right_Specific>button{
  position: absolute;
  width: 44px;
  height: 24px;
  border: 1px solid #cccccc;  
  border-radius: 0px 3px 3px 0px;
  border-left:none;  
  right: -45px;
  margin: 0;
  top: 6px;
  background: linear-gradient(to left, #ffffff 0%,#c1c1c1 100%);
  color: #000000;
}
.Right_Stock{
  border-bottom: 1px solid #cccccc;    
  background: #f8f9fd;
}
.Right_Address{
  background: #f6f6f6;
}
.Right_Address>div:nth-child(1),.Right_Edit>div:nth-child(1){
  width: 407px;
}
.Right_Address>div:nth-child(3),.Right_Edit>div:nth-child(3){
  border-right: none;  
}
.Right_Edit{
  position: relative;
}
.Right_Edit>button{
  width: 18px;
  height: 18px;
  border: 1px solid #cccccc;  
  border-left:none;          
  position: absolute;
  right: -19px;
  margin: 0;
  top: 6px;
  background: #ffffff;
}
.Right_Edit input{
  width: 321px;
  height: 30px;
  margin-left:14px; 
}
.Right_Edit span{
  margin: 11px 22px 5px 22px;
  color: #246ab9;
}
.Right_Edit div:nth-child(3) span{
  color: red;
  margin: 11px 50px 5px 50px;
}

/* 右边边框 */
.b_r{
  border-right: 1px solid #cccccc;    
}
.b_l{
  border-left: 1px solid #cccccc;    
}
.b_t{
  border-top: 1px solid #cccccc;    
}
.b_b{
  border-bottom: 1px solid #cccccc;    
}
</style>

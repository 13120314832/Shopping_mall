<template>
<!-- Basic information  基本信息 -->
  <div class="hello">
    <div class="Bin_Body">
      <div class="Bin_Content">
          <p>商品规格：<span class="Bin_Content_Span">勾选规格后，可修改名称</span></p>
          <!-- 规格 specification-->          
          <div class="Bin_Specification">
            <!-- 颜色 color-->
            <div class="Bin_Color">
              <div class="Bin_Title">
                <span>颜色：</span>
                <button type="button" class="btn_click">管理属性值</button>
              </div>
              <ul>
                <li v-for="(Bin_Color,index) in Bin_Colors":key="index">
                  <img @click="Bin_Color_img(Bin_Color)" class="Bin_Color_Img" :src="Bin_Color.check?'../../static/elect.png':'../../static/unelect.png'">    
                  <!-- <img @click="Bin_Color_img(Bin_Color)" class="Bin_Color_Img" :src="Bin_Color.check?require('./elect.png'):require('./unelect.png')">     -->
                  <span class="Bin_Color_Item_Span" :style="{background:Bin_Color.color}"></span>
                  <span>{{Bin_Color.Bin_Color_Color}}</span>
                </li>
              </ul>
            </div>
            <!-- 尺码 size -->
            <div class="Bin_Size">
              <div class="Bin_Title">
                <span>尺码：</span>
                <button type="button" class="btn_click">管理属性值</button>                
              </div>
              <ul>
                <li v-for="(Bin_Size,index) in Bin_Sizes":key="index">
                  <!-- <img @click="Bin_Size_img(Bin_Size)" class="Bin_Size_Img" :src="Bin_Size.check?require('./elect.png'):require('./unelect.png')">                       -->
                  <img @click="Bin_Size_img(Bin_Size)" class="Bin_Size_Img" :src="Bin_Size.check?'../../static/elect.png':'../../static/unelect.png'">                      
                  <span>{{Bin_Size.Bin_Size_Size}}</span>
                </li>
                <button type="button" class="btn_click" @click="addss('a-component', 'test')">+添加</button>
              </ul>
            </div>
            <!-- 填充 filling -->
            <div class="Bin_Filling">
              <p>该类目下：颜色分类、尺码，请全选或全不选，如果只选一部分则无法保存对应的价格和库存；库存为0的宝贝规格，在商品详情页不展示</p>
              <div>
                <h3>批量填充：</h3>
                <div><span>价格</span><input type="text" name=""></div>
                
                <div><span>数量</span><input type="text" name=""></div>
                <div><span>商家编码</span><input type="text" name=""></div>
                <div><span>条形码</span><input type="text" name=""></div>
                <button type="button" class="btn_click">确定</button>
              </div>
            </div>
            <!-- 分类 classification -->
            <div class="Bin_Cfn">
              <!-- 表头 -->
              <div class="Bin_Cfn_title">
                <div><p>*颜色分类</p></div> 
                <div><p>*尺码</p></div> 
                <div><p>*价格</p></div> 
                <div><p>*SKU图片</p></div> 
                <div><p>商家编码</p></div> 
                <div><p>商品条形码</p></div> 
              </div>
              <!-- 具体内容 -->
              <!-- <CfnBody v-if="showcom"></CfnBody> -->
              <div class="Bin_Cfn_Body" id="Bin_Cfn_Body">
                  <!-- 动态加载 content -->
                  <div class="Bin_Cfn_Body_Content">
                      <!-- 左侧 -->
                      <div class="Bin_Cfn_Body_Content_Left">
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
            </div>
          </div>
      </div>
    </div>
  </div>
</template>
<script>

export default {
  data(){
				return{
					Bin_Colors:[
            {check:false,color:"#fe0000",Bin_Color_Color:"红色"},
            {check:false,color:"#9a0001",Bin_Color_Color:"深红色"},
            {check:false,color:"#fe9900",Bin_Color_Color:"橙色"},
            {check:false,color:"#ffff01",Bin_Color_Color:"黄色"},
            {check:false,color:"#fffe88",Bin_Color_Color:"浅黄色"},
            {check:false,color:"#67cb33",Bin_Color_Color:"浅黄色"},
            {check:false,color:"#339933",Bin_Color_Color:"绿色"},
            {check:false,color:"#0099ff",Bin_Color_Color:"浅蓝色"},
            {check:false,color:"#0033cc",Bin_Color_Color:"蓝色"},
            {check:false,color:"#010066",Bin_Color_Color:"深蓝色"},
            {check:false,color:"#cc99fe",Bin_Color_Color:"浅紫色"},
            {check:false,color:"#660066",Bin_Color_Color:"紫色"},
            {check:false,color:"#ff6666",Bin_Color_Color:"玫瑰红色"},
            {check:false,color:"#fe0000",Bin_Color_Color:"粉红色"},
            {check:false,color:"#f0de94",Bin_Color_Color:"卡其色"},
            {check:false,color:"#9a6600",Bin_Color_Color:"茶色"},
            {check:false,color:"#663200",Bin_Color_Color:"褐色"},
            {check:false,color:"#336600",Bin_Color_Color:"墨绿色"},
            {check:false,color:"#cdffff",Bin_Color_Color:"天蓝色"},
            {check:false,color:"#ff0066",Bin_Color_Color:"荧光色"},
            {check:false,color:"#ffffff",Bin_Color_Color:"白色"},
            {check:false,color:"#cccccc",Bin_Color_Color:"浅灰色"},
            {check:false,color:"#666666",Bin_Color_Color:"灰色"},
            {check:false,color:"#000000",Bin_Color_Color:"黑色"}
          ],
          Bin_Sizes:[
            {check:false,Bin_Size_Size:"S"},
            {check:false,Bin_Size_Size:"M"},
            {check:false,Bin_Size_Size:"L"},
            {check:false,Bin_Size_Size:"XL"}
          ]
        }        
      },
      methods:{
        Bin_Color_img:function(Bin_Color){
          Bin_Color.check = !Bin_Color.check
        },
        Bin_Size_img:function(Bin_Size){
          Bin_Size.check = !Bin_Size.check
        },
      }
}
</script>

<style scoped>
.hello{
  width: 1120px;
  height: 704px;
  background: #edecf0;
  float: left;
}
.Bin_Body{
  margin-left: 15px;
  background: #ffffff;
  width: 1189px;
}
.Bin_Content{
  width: 911px;  
  margin-left: 88px;
}
.Bin_Content>p{
  color: #000000;
  font-size: 14px;
  font-weight: 600;
}
.Bin_Content_Span{
  color: #3276c6;
  font-size: 14px;
}
.Bin_Specification{
  width: 911px;
  height: 704px;
  background: #fafafa;
  border: 1px solid #cccccc;
  margin: 0 auto;
}
.Bin_Color{
  width: 895px;
  height: 192px;
  margin: 0 auto;
}
.Bin_Title{
  width: 100%;
  height: 39px;
  line-height: 39px;
  border-bottom: 1px dashed #cccccc;
}
.Bin_Title>span{
  color: #a8a8a8;
  margin-left: 36px;
}
.Bin_Title>button{
  width: 77px;
  height: 26px;
  margin: 5px auto;
  float: right;  
  -moz-border-radius: 2px;   
  -webkit-border-radius: 2px;    
  border-radius:2px;   
  margin-right: 5px;
  background: #b0b0b0;
  color: #ffffff;
  font-size: 12px;
}
.Bin_Color ul{
  margin-top: 16px;
  padding-left: 14px;
}
.Bin_Color ul li{
  list-style-type: none;
  height: 36px;
  width: 134px;
  margin:0px 6px;
  float: left;
  line-height: 36px;
  font-size: 12px;
}
.Bin_Color_Img{
  margin: 10px 0px;
}
.Bin_Color_Img,.Bin_Size_Img{
  width: 16px;
  float: left;
  height: 16px;
} 
.Bin_Color_Item_Span{
  float: left;
  width: 18px;
  height: 18px;
  margin: 8px 5px 8px 5px;
  border: 1px solid #cccccc;  
}
ul li span{
  float: left;
}
/* 尺码 */
.Bin_Size{
  width: 895px;
  margin: 21px auto 0px;
}
.Bin_Size ul{
  margin-top: 23px;
}
.Bin_Size ul li{
  float: left;
  width: 102px;
  height: 16px;
  line-height: 16px;
  margin-left: 20px;
  margin-top: 3px;
}
.Bin_Size ul li span{
  margin-left: 10px;
}
.Bin_Size ul button{
  width: 53px;
  height: 23px;
  color: #bbbbbb;
  border: 1px solid #cccccc;  
  background: #ffffff;
  -moz-border-radius: 2px;   
  -webkit-border-radius: 2px;    
  border-radius:2px;  
}
.btn_click{
  cursor:pointer;
}
.btn_click:active {                        
  background: #bbbbbb;
  cursor:pointer;
  color: #ffffff;
}
/* 批量填充 */
.Bin_Filling{
  margin: 23px auto 0px;
  width: 895px;
  height: 82px;
}
.Bin_Filling p{
  font-size: 12px;
  color: #a8a8a8;
  line-height: 36px;
  margin: 0 auto;
  text-align:center
}
.Bin_Filling h3{
  font-size: 14px;
  line-height: 33px;
  margin-left: 54px;
  float: left;  
  color: #878787;
}
.Bin_Filling>div>div{
  float: left;
  border: 1px solid #cccccc; 
  margin-left: 10px; 
  
}
.Bin_Filling span{
  display: block;
  float: left;
  padding: 0px 10px;
  height: 33px;
  line-height: 33px;
  color: #a8a8a8;  
  text-align:center  
}
.Bin_Filling input{
  float: left;
  width: 96px;
  height: 33px;
  line-height: 33px;
}
.Bin_Filling button{
  line-height: 23px;
  width: 50px;
  height: 23px;
  margin: 5px 0px 5px 10px;
  border-radius: 2px;
  color: #ffffff;
  background: #b0b0b0;
}
/* 分类 */
.Bin_Cfn{
  width: 815px;
  margin: 16px 71px 0px 25px;
  position: relative;
}
.Bin_Cfn_title{
  border: 1px solid #cccccc;  
  width: 100%;
  height: 30px;
  background: #f6f6f6;
}
.Bin_Cfn_title div,.Bin_Cfn_Body_Content li{
  width: 135px;
  height: 30px;
  float: left;
  border-right: 1px solid #cccccc;
}
.Bin_Cfn_title div:nth-child(6),.Bin_Cfn_Body_Content li:nth-child(6){
  border-right: none;
}
.Bin_Cfn div>p{
  line-height: 30px;
  /* color: #b6b6b6; */
  text-align:center;
}


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
  border-right: 1px solid #cccccc;    
  border-bottom: 1px solid #cccccc; 
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

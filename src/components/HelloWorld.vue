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
                  <img @click="Bin_Color_img(Bin_Color)" 
                  class="Bin_Color_Img" :class="{'active':Bin_Color.show===true}">    
                 <!--  :src="Bin_Color.check?'../../static/elect.png':'../../static/unelect.png'" -->
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
                  <img @click="Bin_Size_img(Bin_Size)" 
                  class="Bin_Size_Img" :class="{'active':Bin_Size.show===true}" >                    
                    <!-- 
                  :src="Bin_Size.check?'../../static/elect.png':'../../static/unelect.png'"
                     -->
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
              <div class="Bin_Cfn_Body" id="Bin_Cfn_Body">
                  <div class="Bin_Cfn_Body_Content">
                      <!-- 左侧 -->
                      <div class="Bin_Cfn_Body_Content_L"  :style="{height:Bin_Cfn_Body_Content_L_h+'px'}">
                        <!-- 动态加载 content -->
                        <div 
                        v-for="(Cfn,index) in D_Color" :key="index" 
                        class="Bin_Cfn_Body_Content_Left" 
                        :style="{height:Bin_Cfn_Body_Content_L_h+'px'}">
                          <div :style="{height:Bin_Cfn_Body_Content_L_h+'px'}">
                              <p id="Left_Color" 
                              :style="{lineHeight:Bin_Cfn_Body_Content_L_h+'px'}"
                              >{{Cfn}}</p>
                          </div>
                          </div>
                      </div>
                      <!-- 右侧 -->
                      <div class="Bin_Cfn_Body_Content_R"  ref="Bin_Cfn_Body_Content_R">
                        <!-- 动态加载 content -->
                        <div v-for="(Cfn,index) in D_Size" :key="index"
                        class="Bin_Cfn_Body_Content_Right">
                          <!-- 第一行 -->
                          <div class="Right_Specific">
                              <div><p>{{Cfn}}</p></div> 
                              <div>
                                <input value="元" 
                                  onfocus="if (value =='元'){value =''}"  
                                  onblur="if (value ==''){value='元'}"  
                                  class="input_ing_one" type="text">
                                </div> 
                              <div><button class="btn_click">+添加图片</button></div> 
                              <div>
                                <input value="|" 
                                  onfocus="if (value =='|'){value =''}"  
                                  onblur="if (value ==''){value='|'}"  
                                  class="input_ing_one" type="text">
                              </div> 
                              <div>
                                <input value="|" 
                                  onfocus="if (value =='|'){value =''}"  
                                  onblur="if (value ==''){value='|'}"  
                                  class="input_ing_one" type="text">
                                </div>
                              <button class="btn_click an_btn" @click="showToggle" v-text="btnText"></button>                                        
                          </div>
                          <!-- 第二三四行 -->
                          <div class="an_div" v-show="isShow">
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
                            <!-- 第四行 应该再包含一层div-->
                            <div class="addition_div">
                              <div class="Right_Edit">
                                  <div><input value="|" 
                                      onfocus="if (value =='|'){value =''}"  
                                      onblur="if (value ==''){value='|'}" 
                                      class="input_ing_two" type="text"><span class="btn_click edit">编辑</span></div>
                                  <div><input value="|" 
                                    onfocus="if (value =='|'){value =''}"  
                                    onblur="if (value ==''){value='|'}"  
                                    class="input_ing_one" type="text"></div>
                                  <div><span class="btn_click deleting">删除</span></div>
                              </div>
                              <!-- 动态 -->
                              <div class="Right_Edit" v-for="(RightEdit,index) in RightEdits":key="index">
                                  <div><input value="|" 
                                      onfocus="if (value =='|'){value =''}"  
                                      onblur="if (value ==''){value='|'}" 
                                      class="input_ing_two" type="text"><span class="btn_click edit">编辑</span></div>
                                  <div><input value="|" 
                                    onfocus="if (value =='|'){value =''}"  
                                    onblur="if (value ==''){value='|'}"  
                                    class="input_ing_one" type="text"></div>
                                  <div><span class="btn_click deleting" @click="Delete(index)">删除</span></div>
                              </div>
                              <button class="btn_click addition_btn" @click="addRightEdit">+</button>  
                            </div>
                          </div>
                          <!-- 第二三四行结束div -->
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
          Cfna:'',
          btnText:"展开》",
          belowHeight: '',
          isShow:false,
          Bin_Cfn_Body_Content_L_h:'',
          D_Color:[],
          D_Size:[],
          RightEdits:[],
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
        // 点击颜色
        Bin_Color_img:function(Bin_Color,index){
          // Bin_Color.check = !Bin_Color.check,//第二次点击 配合切换图片路径
          Bin_Color.show = !Bin_Color.show//点击图片添加class active
          if(Bin_Color.show){//如果是未选中状态，并存入D_Color数组
            this.D_Color.push(//push：在最后面插入
              Bin_Color.Bin_Color_Color//获取颜色传给左侧框中    
            )  
          }else{
            for(var i=0 ; i<this.D_Color.length; i++ ){
              //遍历D_Color数组，判断点击的Bin_Color.Bin_Color_Color是否在数组中，在则删除
              if(Bin_Color.Bin_Color_Color == this.D_Color[i]){
                this.D_Color.splice(i,1)  //删除
              }
            }
          }
        },
        // 点击尺寸
        Bin_Size_img:function(Bin_Size){
          // Bin_Size.check = !Bin_Size.check,//第二次点击 配合切换图片路径
          Bin_Size.show = !Bin_Size.show//点击图片添加class active
          if(Bin_Size.show){
            this.D_Size.push(
              Bin_Size.Bin_Size_Size//获取尺码传给右侧框中 
            ) 
          }else{
            for(var i=0;i<this.D_Size.length;i++ ){
              if(Bin_Size.Bin_Size_Size == this.D_Size[i]){
                this.D_Size.splice(i,1)
              }
            }
          }
        // this.Bin_Cfn_Body_Content_L_h = this.$refs.Bin_Cfn_Body_Content_R.offsetHeight                  
        },
        // 点击展开，收起按钮
        showToggle:function(index){  
            this.isShow = !this.isShow  
            if(this.isShow){  
                this.btnText = "《收起"  
            }else{  
                this.btnText = "展开》"  
            }                         
        },
        // 点击第四行小加号
        addRightEdit:function(){
          this.RightEdits.push({
          })      
        },
        //删除第四行
        Delete:function(index){
          this.RightEdits.splice(index,1)               
        }
      },
       updated () {//钩子 实时加载 左侧等于右侧
        this.Bin_Cfn_Body_Content_L_h = this.$refs.Bin_Cfn_Body_Content_R.offsetHeight - 1
        //获取右侧高度    
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
  background: url(../../static/unelect.png);
  margin: 10px 0px;
}
.active{
  background: url(../../static/elect.png);  
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
  width: 813px;
  height: 30px;
  background: #f6f6f6;
}
.Bin_Cfn_title div,.Bin_Cfn_Body_Content li{
  width: 134px;
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
  border-top: none;
}
.Bin_Cfn_Body_Content{
  width: 100%;
  height: 100%;
}
.Bin_Cfn_Body_Content_L{
  width: 136px;
  float: left;

}
.Bin_Cfn_Body_Content_R{
  width: 679px;
  float: right;
  
}
.Bin_Cfn_Body_Content_Left{
  width: 134px;
  float: left;
  border-right: 1px solid #cccccc;    
  border-left: 1px solid #cccccc;    
  border-bottom: 1px solid #cccccc; 
  /* 30 61 92 123 */  
  height: 30px;
}
.Bin_Cfn_Body_Content_Left div{
  width: 100%;
  height: 30px;
  /* 30 61 92 123 */  
  text-align: center;
  border-bottom: 1px solid #cccccc;      
}
#Left_Color{
  line-height: 30px;
  /* 30 61 92 123 */
}
.Bin_Cfn_Body_Content div p{
  font-size: 12px;
  line-height: 30px;
  color: #b6b6b6;
}
.Bin_Cfn_Body_Content div span{
  font-size: 12px;
  /* line-height: 30px; */
  text-decoration:underline;
}
.Bin_Cfn_Body_Content_Right{
  width: 678px;
  float: left;
  border-right: 1px solid #cccccc;      
  border-left: 1px solid #cccccc;     
  margin-left:-1px;  
}
.Right_Specific{
  border-bottom: 1px solid #cccccc;  
  width: 100%;
  height: 30px;
}
.Right_Specific>div{
  width: 135px;
  float: left;
  border-right: 1px solid #cccccc;    
  margin-left: -1px;   
  height: 30px;
}
.Bin_Cfn_Body_Content_Right>div>div:nth-child(5){
  border-right: none;    
}
.Right_Specific button{
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
  top: 4px;
  background: linear-gradient(to left, #ffffff 0%,#c1c1c1 100%);
  color: #000000;
}
/* 展开 */
.an_div{
  width: 100%;
}
.addition_div{
  position: relative;
}
.Right_Stock,.Right_Address,.Right_Edit{
  height: 30px;
  width: 100%;
  border-bottom: 1px solid #cccccc;   
}
.Right_Address>div,.Right_Edit>div{
  width: 134px;
  height: 30px;
  float: left;
  overflow: hidden;
  border-right: 1px solid #cccccc;  
}
/* 第二行 */
.Right_Stock{
  border-bottom: 1px solid #cccccc;    
  background: #f8f9fd;
}
/* 第三行 */
.Right_Address{
  background: #f6f6f6;
}
.Right_Address>div:nth-child(1),.Right_Edit>div:nth-child(1){
  width: 405px;
}
.Right_Address>div:nth-child(3),.Right_Edit>div:nth-child(3){
  border-right: none;
}
/* 第四行 */
.Right_Edit{
  position: relative;
}
.Right_Edit div{
   line-height: 30px;
}
.addition_btn{
  width: 18px;
  height: 18px;
  border: 1px solid #cccccc;  
  border-left:none;          
  position: absolute;
  right: -19px;
  margin: 0;
  bottom: 6px;
  background: #ffffff;
}
.input_ing_two{
  width: 321px;
  height: 30px;
  margin-left:14px; 
  color: #b6b6b6;
  float: left;
}
.input_ing_one{
  width: 115px;
  margin: 0 10px;
  height: 30px;
  color: #b6b6b6;
}
.Right_Edit .edit{
  text-align:center;/*span中的文字居中 */
  width: 70px;
  height: 30px;
  float: left;
  color: #246ab9;
  display: block;  
}
.Right_Edit .deleting{
  color: red;
  /* margin: 7px 55px 5px 55px; */
  width: 134px;
  height: 30px;
  display: block;
  text-align:center;
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

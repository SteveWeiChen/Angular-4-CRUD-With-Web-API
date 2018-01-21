# Angular-4-CRUD-With-Web-API

Before running this project
1. Web API : Edit Web.config -> Connection String as Per Your SQL Server
2. Create SQL Server DB Using the DB Script
3. Angular 4 : Install npm packages using 'npm install' command

ng new angularCURD  //创建angular项目
cd angularCURD
ng serve --open  //启动服务并打开浏览器localhost://4200
生成的.spec.ts文件是用于测试的,可以删除.
ng g class employee.model 生成employee.model.ts文件.
app-emplloyees按下tab键,生成<app-emplloyees></app-emplloyees>
h2.jumbotron.bg-secondary.text-white按下tab键,生成<h2 class="jumbotron bg-secondary text-white"></h2>   //多个class之间用.
<input class="form-control" name="Office" #Office="ngModel" [(ngModel)]="employee" />  //#Office="ngModel"用于验证

解决webapi跨域访问的问题: 安装组件Microsoft.AspNet.WebApi.Cors, 地址 https://www.nuget.org/packages/Microsoft.AspNet.WebApi.Cors ,命令是Install-Package Microsoft.AspNet.WebApi.Cors -Version 5.2.3 之后代码:
using System.Web.Http.Cors;
[EnableCors(origins: "http://localhost:4200",headers:"*",methods:"*")]    //加到public class EmployeeControler: ApiController之上
上面是针对指定controller, 加到WebApiConfig.cs文件的Register方法下可以针对整个项目有效.
页面报错的话执行代码Install-Package Microsoft.AspNet.WebApi.Core -Version 5.2.3

安装toastr插件: npm install ngx-toastr --save, 地址https://www.npmjs.com/package/ngx-toastr,
.angular-cli.json中的"styles"节点下添加"../node_modules/ngx-toastr/toastr.css"
app.modules.ts中:
import {ToastrModule} from 'ngx-toastr';
imports:[
	ToastrModule.forRoot()
]
emplloyees.component.ts中:
import {ToastrService} from 'ngx-toastr'
constructor(private toastr:ToastrService)
this.toastr.success('New Record Added Successfully','Employee Register')

# Angular-4-CRUD-With-Web-API-master

Before running this project111
1. Web API : Edit Web.config -> Connection String as Per Your SQL Server
2. Create SQL Server DB Using the DB Script
3. Angular 4 : Install npm packages using 'npm install' command

ng new angularCURD  //创建angular项目<br/>
cd angularCURD<br/>
ng serve --open  //启动服务并打开浏览器localhost://4200<br/>
生成的.spec.ts文件是用于测试的,可以删除.<br/>
ng g class employee.model 生成employee.model.ts文件.<br/>
<input class="form-control" name="Office" #Office="ngModel" [(ngModel)]="employee" />  //#Office="ngModel"用于验证<br/><br/>

解决webapi跨域访问的问题: 安装组件Microsoft.AspNet.WebApi.Cors, 地址 https://www.nuget.org/packages/Microsoft.AspNet.WebApi.Cors ,命令是Install-Package Microsoft.AspNet.WebApi.Cors -Version 5.2.3 之后代码:<br/>
using System.Web.Http.Cors;<br/>
[EnableCors(origins: "http://localhost:4200",headers:"*",methods:"*")]    //加到public class EmployeeControler: ApiController之上<br/>
上面是针对指定controller, 加到WebApiConfig.cs文件的Register方法下可以针对整个项目有效.<br/>
页面报错的话执行代码Install-Package Microsoft.AspNet.WebApi.Core -Version 5.2.3<br/><br/>

安装toastr插件: npm install ngx-toastr --save, 地址https://www.npmjs.com/package/ngx-toastr,<br/>
.angular-cli.json中的"styles"节点下添加"../node_modules/ngx-toastr/toastr.css"<br/>
app.modules.ts中:<br/>
import {ToastrModule} from 'ngx-toastr';<br/>
imports:[
	ToastrModule.forRoot()
]<br/>
emplloyees.component.ts中:<br/>
import {ToastrService} from 'ngx-toastr'<br/>
constructor(private toastr:ToastrService)<br/>
this.toastr.success('New Record Added Successfully','Employee Register')<br/>

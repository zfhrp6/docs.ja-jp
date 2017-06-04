---
title: "SendMail カスタム アクティビティ | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 947a9ae6-379c-43a3-9cd5-87f573a5739f
caps.latest.revision: 11
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 11
---
# SendMail カスタム アクティビティ
このサンプルでは、<xref:System.Activities.AsyncCodeActivity> から派生するカスタム アクティビティを作成して、SMTP を使用して電子メールを送信し、ワークフロー アプリケーション内で使用する方法を示します。カスタム アクティビティは <xref:System.Net.Mail.SmtpClient> の機能を使用して、電子メールを非同期的に送信したり、電子メールを認証付きで送信します。また、テスト モード、トークン置換、ファイル テンプレート、テスト ドロップ パスなどのエンドユーザーの機能も提供しています。  
  
 次の表で、`SendMail` アクティビティの引数の詳細を説明します。  
  
||||  
|-|-|-|  
|名前|型|説明|  
|Host|文字列|SMTP サーバー ホストのアドレス。|  
|Port|文字列|ホストの SMTP サービスのポート。|  
|EnableSsl|ブール値|<xref:System.Net.Mail.SmtpClient> が、接続を暗号化するために SSL \(Secure Sockets Layer\) を使用するかどうかを指定します。|  
|UserName|文字列|差出人の <xref:System.Net.Mail.SmtpClient.Credentials%2A> プロパティを認証する資格情報を設定するユーザー名。|  
|Password|文字列|差出人の <xref:System.Net.Mail.SmtpClient.Credentials%2A> プロパティを認証する資格情報を設定するパスワード。|  
|Subject|<xref:System.Activities.InArgument%601>\<文字列\>|メッセージの件名。|  
|Body|<xref:System.Activities.InArgument%601>\<文字列\>|メッセージの本文。|  
|Attachments|<xref:System.Activities.InArgument%601>\<文字列\>|この電子メール メッセージに添付されるデータの格納に使用される添付データのコレクション。|  
|From|<xref:System.Net.Mail.MailAddress>|この電子メール メッセージの差出人アドレス。|  
|To|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>\>|この電子メール メッセージの受信者を格納するアドレスのコレクション。|  
|CC|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>\>|この電子メール メッセージの CC \(carbon copy\) 受信者を格納するアドレスのコレクション。|  
|BCC|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>\>|この電子メール メッセージの BCC \(blind carbon copy\) 受信者を格納するアドレスのコレクション。|  
|Tokens|<xref:System.Activities.InArgument%601>\<IDictionary\<文字列,文字列\>\>|本文で置換するトークン。この機能を使用すると、本文にいくつかの値を指定した後、このプロパティを使用して提供されるトークンで置換できます。|  
|BodyTemplateFilePath|文字列|本文のテンプレートのパス。`SendMail` アクティビティは、このファイルの内容をその body プロパティにコピーします。<br /><br /> テンプレートは、tokens プロパティの内容によって置き換えられるトークンを含めることができます。|  
|TestMailTo|<xref:System.Net.Mail.MailAddress>|このプロパティを設定すると、すべての電子メールがそのプロパティで指定されているアドレスに送信されます。<br /><br /> このプロパティは、ワークフローをテストするときに使用するためのものです。たとえば、実際の受信者に送信せずに、すべての電子メールが送信されることを確認します。|  
|TestDropPath|文字列|このプロパティを設定すると、すべての電子メールが指定したファイルにも保存されます。<br /><br /> このプロパティは、ワークフローのテストやデバッグを行うときに使用したり、送信する電子メールの形式や内容が適切であることを確認するためのものです。|  
  
## ソリューションのコンテンツ  
 ソリューションには、次の 2 つのプロジェクトが含まれています。  
  
|プロジェクト|説明|重要なファイル|  
|------------|--------|-------------|  
|SendMail|SendMail アクティビティ|1.  SendMail.cs: main アクティビティの実装<br />2.  SendMailDesigner.xaml および SendMailDesigner.xaml.cs: SendMail アクティビティのデザイナー<br />3.  MailTemplateBody.htm: 送信される電子メールのテンプレート|  
|SendMailTestClient|SendMail アクティビティをテストするクライアント。このプロジェクトでは、SendMail アクティビティを宣言的に起動する方法とプログラムで起動する方法を示します。|1.  Sequence1.xaml: SendMail アクティビティを起動するワークフロー<br />2.  Program.cs: Sequence1 を呼び出し、SendMail を使用するワークフローもプログラムで作成します。|  
  
## SendMail アクティビティの追加構成  
 サンプルには表示されませんが、SendMail アクティビティの追加構成を実行できます。次の 3 つのセクションは、その方法を示しています。  
  
### 本文で指定されたトークンを使用した電子メールの送信  
 次のコード スニペットでは、本文のトークンを使用して電子メールを送信する方法を示します。トークンが body プロパティに指定されていることに注目してください。それらのトークンの値は、tokens プロパティに指定されています。  
  
```html  
IDictionary<string, string> tokens = new Dictionary<string, string>();  
tokens.Add("@name", "John Doe");  
tokens.Add("@date", DateTime.Now.ToString());  
tokens.Add("@server", "localhost");  
  
new SendMail  
{  
    From = new LambdaValue<MailAddress>(ctx => new MailAddress("john.doe@contoso.com")),  
    To = new LambdaValue<MailAddressCollection>(  
                    ctx => new MailAddressCollection() { new MailAddress("someone@microsoft.com") }),  
    Subject = "Test email",  
    Body = "Hello @name. This is a test email sent from @server. Current date is @date",  
    Host = "localhost",  
    Port = 25,  
    Tokens = new LambdaValue<IDictionary<string, string>>(ctx => tokens)  
};  
  
```  
  
### テンプレートを使用した電子メールの送信  
 次のスニペットでは、本文のテンプレート トークンを使用して電子メールを送信する方法を示します。`BodyTemplateFilePath` プロパティを設定するときに、Body プロパティの値を指定する必要がないことに注目してください \(テンプレート ファイルのコンテンツは本文にコピーされます\)。  
  
```  
new SendMail  
{    
    From = new LambdaValue<MailAddress>(ctx => new MailAddress("john.doe@contoso.com")),  
    To = new LambdaValue<MailAddressCollection>(  
                    ctx => new MailAddressCollection() { new MailAddress("someone@microsoft.com") }),  
    Subject = "Test email",  
    Host = "localhost",  
    Port = 25,  
    Tokens = new LambdaValue<IDictionary<string, string>>(ctx => tokens),  
    BodyTemplateFilePath = @"..\..\..\SendMail\Templates\MailTemplateBody.htm",   
};  
  
```  
  
### テスト モードでの電子メールの送信  
 次のコード スニペットでは、2 つのテスト プロパティを設定する方法を示します。すべてのメッセージに `TestMailTo` を設定すると、\(To、Cc、Bcc の値に関係なく\) john.doe@contoso.con に送信されます。TestDropPath を設定すると、送信するすべての電子メールは、指定したパスにも記録されます。これらのプロパティは、個別に設定できます \(関連していません\)。  
  
```  
new SendMail  
{    
   From = new LambdaValue<MailAddress>(ctx => new MailAddress("john.doe@contoso.com")),  
   To = new LambdaValue<MailAddressCollection>(  
                    ctx => new MailAddressCollection() { new MailAddress("someone@microsoft.com") }),  
   Subject = "Test email",  
   Host = "localhost",  
   Port = 25,  
   Tokens = new LambdaValue<IDictionary<string, string>>(ctx => tokens),  
   BodyTemplateFilePath = @"..\..\..\SendMail\Templates\MailTemplateBody.htm",  
   TestMailTo= new LambdaValue<MailAddress>(ctx => new MailAddress("john.doe@contoso.com")),  
   TestDropPath = @"c:\Samples\SendMail\TestDropPath\",  
};  
  
```  
  
## セットアップ手順  
 このサンプルでは SMTP サーバーにアクセスする必要があります。  
  
 SMTP サーバーの設定[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、次のリンクを参照してください。  
  
-   [Microsoft Technet](http://go.microsoft.com/fwlink/?LinkId=166060)  
  
-   [SMTP サービス \(IIS 6.0\) の構成](http://go.microsoft.com/fwlink/?LinkId=150456)  
  
-   [IIS 7.0: SMTP 電子メールの構成](http://go.microsoft.com/fwlink/?LinkId=150457)  
  
-   [SMTP サービスをインストールする方法](http://go.microsoft.com/fwlink/?LinkId=150458)  
  
 ダウンロードには、サードパーティで提供されている SMTP エミュレーターを使用できます。  
  
##### このサンプルを実行するには  
  
1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を使用して、SendMail.sln ソリューション ファイルを開きます。  
  
2.  有効な SMTP サーバーへのアクセス権があることを確認してください。セットアップ手順を参照してください。  
  
3.  サーバー アドレスと電子メールの差出人アドレスおよび宛先アドレスを使用してプログラムを構成します。  
  
     このサンプルを正しく実行するには、電子メールの差出人アドレスおよび宛先アドレスの値と Program.cs および Sequence.xaml の SMTP サーバーのアドレスを設定する必要がある場合があります。プログラムでは電子メールが 2 つの方法で送信されるため、両方の場所でアドレスを変更する必要があります。  
  
4.  ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。  
  
5.  ソリューションを実行するには、Ctrl キーを押しながら F5 キーを押します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\SendMail`  
  
## 参照
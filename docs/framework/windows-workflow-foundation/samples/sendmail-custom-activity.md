---
title: "SendMail カスタム アクティビティ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 947a9ae6-379c-43a3-9cd5-87f573a5739f
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: bffca162bfa7bf5a4d2b1bf23566f2b039391f4c
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/28/2017
---
# <a name="sendmail-custom-activity"></a><span data-ttu-id="25724-102">SendMail カスタム アクティビティ</span><span class="sxs-lookup"><span data-stu-id="25724-102">SendMail Custom Activity</span></span>
<span data-ttu-id="25724-103">このサンプルでは、<xref:System.Activities.AsyncCodeActivity> から派生するカスタム アクティビティを作成して、SMTP を使用して電子メールを送信し、ワークフロー アプリケーション内で使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="25724-103">This sample demonstrates how to create a custom activity that derives from <xref:System.Activities.AsyncCodeActivity> to send mail using SMTP for use within a workflow application.</span></span> <span data-ttu-id="25724-104">カスタム アクティビティは <xref:System.Net.Mail.SmtpClient> の機能を使用して、電子メールを非同期的に送信したり、電子メールを認証付きで送信します。</span><span class="sxs-lookup"><span data-stu-id="25724-104">The custom activity uses the capabilities of <xref:System.Net.Mail.SmtpClient> to send e-mail asynchronously and to send mail with authentication.</span></span> <span data-ttu-id="25724-105">また、テスト モード、トークン置換、ファイル テンプレート、テスト ドロップ パスなどのエンドユーザーの機能も提供しています。</span><span class="sxs-lookup"><span data-stu-id="25724-105">It also provides some end-user features like test mode, token replacement, file templates, and test drop path.</span></span>  
  
 <span data-ttu-id="25724-106">次の表で、`SendMail` アクティビティの引数の詳細を説明します。</span><span class="sxs-lookup"><span data-stu-id="25724-106">The following table details the arguments for the `SendMail` activity.</span></span>  
  
|<span data-ttu-id="25724-107">名前</span><span class="sxs-lookup"><span data-stu-id="25724-107">Name</span></span>|<span data-ttu-id="25724-108">種類</span><span class="sxs-lookup"><span data-stu-id="25724-108">Type</span></span>|<span data-ttu-id="25724-109">説明</span><span class="sxs-lookup"><span data-stu-id="25724-109">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="25724-110">Host</span><span class="sxs-lookup"><span data-stu-id="25724-110">Host</span></span>|<span data-ttu-id="25724-111">String</span><span class="sxs-lookup"><span data-stu-id="25724-111">String</span></span>|<span data-ttu-id="25724-112">SMTP サーバー ホストのアドレス。</span><span class="sxs-lookup"><span data-stu-id="25724-112">Address of the SMTP server host.</span></span>|  
|<span data-ttu-id="25724-113">ポート</span><span class="sxs-lookup"><span data-stu-id="25724-113">Port</span></span>|<span data-ttu-id="25724-114">String</span><span class="sxs-lookup"><span data-stu-id="25724-114">String</span></span>|<span data-ttu-id="25724-115">ホストの SMTP サービスのポート。</span><span class="sxs-lookup"><span data-stu-id="25724-115">Port of the SMTP service in the host.</span></span>|  
|<span data-ttu-id="25724-116">EnableSsl</span><span class="sxs-lookup"><span data-stu-id="25724-116">EnableSsl</span></span>|<span data-ttu-id="25724-117">bool</span><span class="sxs-lookup"><span data-stu-id="25724-117">bool</span></span>|<span data-ttu-id="25724-118"><xref:System.Net.Mail.SmtpClient> が、接続を暗号化するために SSL (Secure Sockets Layer) を使用するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="25724-118">Specifies whether the <xref:System.Net.Mail.SmtpClient> uses Secure Sockets Layer (SSL) to encrypt the connection.</span></span>|  
|<span data-ttu-id="25724-119">UserName</span><span class="sxs-lookup"><span data-stu-id="25724-119">UserName</span></span>|<span data-ttu-id="25724-120">String</span><span class="sxs-lookup"><span data-stu-id="25724-120">String</span></span>|<span data-ttu-id="25724-121">差出人の <xref:System.Net.Mail.SmtpClient.Credentials%2A> プロパティを認証する資格情報を設定するユーザー名。</span><span class="sxs-lookup"><span data-stu-id="25724-121">Username to set up the credentials to authenticate the sender <xref:System.Net.Mail.SmtpClient.Credentials%2A> property.</span></span>|  
|<span data-ttu-id="25724-122">[Password]</span><span class="sxs-lookup"><span data-stu-id="25724-122">Password</span></span>|<span data-ttu-id="25724-123">String</span><span class="sxs-lookup"><span data-stu-id="25724-123">String</span></span>|<span data-ttu-id="25724-124">差出人の <xref:System.Net.Mail.SmtpClient.Credentials%2A> プロパティを認証する資格情報を設定するパスワード。</span><span class="sxs-lookup"><span data-stu-id="25724-124">Password to set up the credentials to authenticate the sender <xref:System.Net.Mail.SmtpClient.Credentials%2A> property.</span></span>|  
|<span data-ttu-id="25724-125">Subject</span><span class="sxs-lookup"><span data-stu-id="25724-125">Subject</span></span>|<span data-ttu-id="25724-126"><xref:System.Activities.InArgument%601>\<文字列 ></span><span class="sxs-lookup"><span data-stu-id="25724-126"><xref:System.Activities.InArgument%601>\<string></span></span>|<span data-ttu-id="25724-127">メッセージの件名。</span><span class="sxs-lookup"><span data-stu-id="25724-127">Subject of the message.</span></span>|  
|<span data-ttu-id="25724-128">Body</span><span class="sxs-lookup"><span data-stu-id="25724-128">Body</span></span>|<span data-ttu-id="25724-129"><xref:System.Activities.InArgument%601>\<文字列 ></span><span class="sxs-lookup"><span data-stu-id="25724-129"><xref:System.Activities.InArgument%601>\<string></span></span>|<span data-ttu-id="25724-130">メッセージの本文。</span><span class="sxs-lookup"><span data-stu-id="25724-130">Body of the message.</span></span>|  
|<span data-ttu-id="25724-131">Attachments</span><span class="sxs-lookup"><span data-stu-id="25724-131">Attachments</span></span>|<span data-ttu-id="25724-132"><xref:System.Activities.InArgument%601>\<文字列 ></span><span class="sxs-lookup"><span data-stu-id="25724-132"><xref:System.Activities.InArgument%601>\<string></span></span>|<span data-ttu-id="25724-133">この電子メール メッセージに添付されるデータの格納に使用される添付データのコレクション。</span><span class="sxs-lookup"><span data-stu-id="25724-133">Attachment collection used to store data attached to this e-mail message.</span></span>|  
|<span data-ttu-id="25724-134">変換前</span><span class="sxs-lookup"><span data-stu-id="25724-134">From</span></span>|<xref:System.Net.Mail.MailAddress>|<span data-ttu-id="25724-135">この電子メール メッセージの差出人アドレス。</span><span class="sxs-lookup"><span data-stu-id="25724-135">From address for this e-mail message.</span></span>|  
|<span data-ttu-id="25724-136">終了</span><span class="sxs-lookup"><span data-stu-id="25724-136">To</span></span>|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|<span data-ttu-id="25724-137">この電子メール メッセージの受信者を格納するアドレスのコレクション。</span><span class="sxs-lookup"><span data-stu-id="25724-137">Address collection that contains the recipients of this e-mail message.</span></span>|  
|<span data-ttu-id="25724-138">CC</span><span class="sxs-lookup"><span data-stu-id="25724-138">CC</span></span>|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|<span data-ttu-id="25724-139">この電子メール メッセージの CC (carbon copy) 受信者を格納するアドレスのコレクション。</span><span class="sxs-lookup"><span data-stu-id="25724-139">Address collection that contains the carbon copy (CC) recipients for this e-mail message.</span></span>|  
|<span data-ttu-id="25724-140">BCC</span><span class="sxs-lookup"><span data-stu-id="25724-140">BCC</span></span>|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|<span data-ttu-id="25724-141">この電子メール メッセージの BCC (blind carbon copy) 受信者を格納するアドレスのコレクション。</span><span class="sxs-lookup"><span data-stu-id="25724-141">Address collection that contains the blind carbon copy (BCC) recipients for this e-mail message.</span></span>|  
|<span data-ttu-id="25724-142">トークン</span><span class="sxs-lookup"><span data-stu-id="25724-142">Tokens</span></span>|<span data-ttu-id="25724-143"><xref:System.Activities.InArgument%601>< IDictionary\<, string >></span><span class="sxs-lookup"><span data-stu-id="25724-143"><xref:System.Activities.InArgument%601><IDictionary\<string, string>></span></span>|<span data-ttu-id="25724-144">本文で置換するトークン。</span><span class="sxs-lookup"><span data-stu-id="25724-144">Tokens to replace in the body.</span></span> <span data-ttu-id="25724-145">この機能を使用すると、本文にいくつかの値を指定した後、このプロパティを使用して提供されるトークンで置換できます。</span><span class="sxs-lookup"><span data-stu-id="25724-145">This feature allows users to specify some values in the body than can be replaced later by the tokens provided using this property.</span></span>|  
|<span data-ttu-id="25724-146">BodyTemplateFilePath</span><span class="sxs-lookup"><span data-stu-id="25724-146">BodyTemplateFilePath</span></span>|<span data-ttu-id="25724-147">String</span><span class="sxs-lookup"><span data-stu-id="25724-147">String</span></span>|<span data-ttu-id="25724-148">本文のテンプレートのパス。</span><span class="sxs-lookup"><span data-stu-id="25724-148">Path of a template for the body.</span></span> <span data-ttu-id="25724-149">`SendMail` アクティビティは、このファイルの内容をその body プロパティにコピーします。</span><span class="sxs-lookup"><span data-stu-id="25724-149">The `SendMail` activity copies the contents of this file to its body property.</span></span><br /><br /> <span data-ttu-id="25724-150">テンプレートは、tokens プロパティの内容によって置き換えられるトークンを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="25724-150">The template can contain tokens that are replaced by the contents of the tokens property.</span></span>|  
|<span data-ttu-id="25724-151">TestMailTo</span><span class="sxs-lookup"><span data-stu-id="25724-151">TestMailTo</span></span>|<xref:System.Net.Mail.MailAddress>|<span data-ttu-id="25724-152">このプロパティを設定すると、すべての電子メールがそのプロパティで指定されているアドレスに送信されます。</span><span class="sxs-lookup"><span data-stu-id="25724-152">When this property is set, all e-mails are sent to the address specified in it.</span></span><br /><br /> <span data-ttu-id="25724-153">このプロパティは、ワークフローをテストするときに使用するためのものです。</span><span class="sxs-lookup"><span data-stu-id="25724-153">This property is intended to be used when testing workflows.</span></span> <span data-ttu-id="25724-154">たとえば、実際の受信者に送信せずに、すべての電子メールが送信されることを確認します。</span><span class="sxs-lookup"><span data-stu-id="25724-154">For example, when you want to make sure that all e-mails are sent without sending them to the actual recipients.</span></span>|  
|<span data-ttu-id="25724-155">TestDropPath</span><span class="sxs-lookup"><span data-stu-id="25724-155">TestDropPath</span></span>|<span data-ttu-id="25724-156">String</span><span class="sxs-lookup"><span data-stu-id="25724-156">String</span></span>|<span data-ttu-id="25724-157">このプロパティを設定すると、すべての電子メールが指定したファイルにも保存されます。</span><span class="sxs-lookup"><span data-stu-id="25724-157">When this property is set, all e-mails are also saved in the specified file.</span></span><br /><br /> <span data-ttu-id="25724-158">このプロパティは、ワークフローのテストやデバッグを行うときに使用したり、送信する電子メールの形式や内容が適切であることを確認するためのものです。</span><span class="sxs-lookup"><span data-stu-id="25724-158">This property is intended to be used when you are testing or debugging workflows, to make sure that the format and contents of the outgoing e-mails is appropriate.</span></span>|  
  
## <a name="solution-contents"></a><span data-ttu-id="25724-159">ソリューションのコンテンツ</span><span class="sxs-lookup"><span data-stu-id="25724-159">Solution Contents</span></span>  
 <span data-ttu-id="25724-160">ソリューションには、次の 2 つのプロジェクトが含まれています。</span><span class="sxs-lookup"><span data-stu-id="25724-160">The solution contains two projects.</span></span>  
  
|<span data-ttu-id="25724-161">プロジェクト</span><span class="sxs-lookup"><span data-stu-id="25724-161">Project</span></span>|<span data-ttu-id="25724-162">説明</span><span class="sxs-lookup"><span data-stu-id="25724-162">Description</span></span>|<span data-ttu-id="25724-163">重要なファイル</span><span class="sxs-lookup"><span data-stu-id="25724-163">Important Files</span></span>|  
|-------------|-----------------|---------------------|  
|<span data-ttu-id="25724-164">SendMail</span><span class="sxs-lookup"><span data-stu-id="25724-164">SendMail</span></span>|<span data-ttu-id="25724-165">SendMail アクティビティ</span><span class="sxs-lookup"><span data-stu-id="25724-165">The SendMail activity</span></span>|<span data-ttu-id="25724-166">1.SendMail.cs: main アクティビティの実装</span><span class="sxs-lookup"><span data-stu-id="25724-166">1.  SendMail.cs: implementation for the main activity</span></span><br /><span data-ttu-id="25724-167">2.SendMailDesigner.xaml および SendMailDesigner.xaml.cs: SendMail アクティビティのデザイナー</span><span class="sxs-lookup"><span data-stu-id="25724-167">2.  SendMailDesigner.xaml and SendMailDesigner.xaml.cs: designer for the SendMail activity</span></span><br /><span data-ttu-id="25724-168">3.MailTemplateBody.htm: 送信される電子メールのテンプレート</span><span class="sxs-lookup"><span data-stu-id="25724-168">3.  MailTemplateBody.htm: template for the email to be sent out.</span></span>|  
|<span data-ttu-id="25724-169">SendMailTestClient</span><span class="sxs-lookup"><span data-stu-id="25724-169">SendMailTestClient</span></span>|<span data-ttu-id="25724-170">SendMail アクティビティをテストするクライアント。</span><span class="sxs-lookup"><span data-stu-id="25724-170">Client to test the SendMail activity.</span></span>  <span data-ttu-id="25724-171">このプロジェクトでは、SendMail アクティビティを宣言的に起動する方法とプログラムで起動する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="25724-171">This project demonstrates two ways of invoking the SendMail activity: declaratively, and programmatically.</span></span>|<span data-ttu-id="25724-172">1.Sequence1.xaml: SendMail アクティビティを起動するワークフロー</span><span class="sxs-lookup"><span data-stu-id="25724-172">1.  Sequence1.xaml: workflow that invokes the SendMail activity.</span></span><br /><span data-ttu-id="25724-173">2.Program.cs: Sequence1 を呼び出し、SendMail を使用するワークフローもプログラムで作成します。</span><span class="sxs-lookup"><span data-stu-id="25724-173">2.  Program.cs: invokes Sequence1 and also creates a workflow programmatically that uses SendMail.</span></span>|  
  
## <a name="further-configuration-of-the-sendmail-activity"></a><span data-ttu-id="25724-174">SendMail アクティビティの追加構成</span><span class="sxs-lookup"><span data-stu-id="25724-174">Further configuration of the SendMail activity</span></span>  
 <span data-ttu-id="25724-175">サンプルには表示されませんが、SendMail アクティビティの追加構成を実行できます。</span><span class="sxs-lookup"><span data-stu-id="25724-175">Although not shown in the sample, users can perform addition configuration of the SendMail activity.</span></span> <span data-ttu-id="25724-176">次の 3 つのセクションは、その方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="25724-176">The next three sections demonstrate how this is done.</span></span>  
  
### <a name="sending-an-email-using-tokens-specified-in-the-body"></a><span data-ttu-id="25724-177">本文で指定されたトークンを使用した電子メールの送信</span><span class="sxs-lookup"><span data-stu-id="25724-177">Sending an email using tokens specified in the body</span></span>  
 <span data-ttu-id="25724-178">次のコード スニペットでは、本文のトークンを使用して電子メールを送信する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="25724-178">This code snippet demonstrates how you can send email with tokens in the body.</span></span> <span data-ttu-id="25724-179">トークンが body プロパティに指定されていることに注目してください。</span><span class="sxs-lookup"><span data-stu-id="25724-179">Notice how the tokens are provided in the body property.</span></span> <span data-ttu-id="25724-180">それらのトークンの値は、tokens プロパティに指定されています。</span><span class="sxs-lookup"><span data-stu-id="25724-180">Values for those tokens are provided to the tokens property.</span></span>  
  
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
  
### <a name="sending-an-email-using-a-template"></a><span data-ttu-id="25724-181">テンプレートを使用した電子メールの送信</span><span class="sxs-lookup"><span data-stu-id="25724-181">Sending an email using a template</span></span>  
 <span data-ttu-id="25724-182">次のスニペットでは、本文のテンプレート トークンを使用して電子メールを送信する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="25724-182">This snippet shows how to send an email using a template tokens in the body.</span></span> <span data-ttu-id="25724-183">`BodyTemplateFilePath` プロパティを設定するときに、Body プロパティの値を指定する必要がないことに注目してください (テンプレート ファイルのコンテンツは本文にコピーされます)。</span><span class="sxs-lookup"><span data-stu-id="25724-183">Notice that when setting the `BodyTemplateFilePath` property we don’t need to provide the value for Body property (the contents of the template file will be copied to the body).</span></span>  
  
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
  
### <a name="sending-mails-in-testing-mode"></a><span data-ttu-id="25724-184">テスト モードでの電子メールの送信</span><span class="sxs-lookup"><span data-stu-id="25724-184">Sending Mails in Testing Mode</span></span>  
 <span data-ttu-id="25724-185">このコード スニペットは、2 つのテストのプロパティを設定する方法を示します: を設定して`TestMailTo`すべてのメッセージを送信する送信先にjohn.doe@contoso.con(なし、To、Cc、Bcc の値の関係)。</span><span class="sxs-lookup"><span data-stu-id="25724-185">This code snippet shows how to set the two testing properties: by setting `TestMailTo` to all messages will be sent to john.doe@contoso.con (without regard of the values of To, Cc, Bcc).</span></span> <span data-ttu-id="25724-186">TestDropPath を設定すると、送信するすべての電子メールは、指定したパスにも記録されます。</span><span class="sxs-lookup"><span data-stu-id="25724-186">By setting TestDropPath all outgoing emails will be also recorded in the provided path.</span></span> <span data-ttu-id="25724-187">これらのプロパティは、個別に設定できます (関連していません)。</span><span class="sxs-lookup"><span data-stu-id="25724-187">These properties can be set independently (they are not related).</span></span>  
  
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
  
## <a name="set-up-instructions"></a><span data-ttu-id="25724-188">セットアップ手順</span><span class="sxs-lookup"><span data-stu-id="25724-188">Set-Up Instructions</span></span>  
 <span data-ttu-id="25724-189">このサンプルでは SMTP サーバーにアクセスする必要があります。</span><span class="sxs-lookup"><span data-stu-id="25724-189">Access to a SMTP server is required for this sample.</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="25724-190">SMTP サーバーをセットアップすると、次のリンクが表示されます。</span><span class="sxs-lookup"><span data-stu-id="25724-190"> setting up a SMTP server, see the following links.</span></span>  
  
-   [<span data-ttu-id="25724-191">Microsoft Technet</span><span class="sxs-lookup"><span data-stu-id="25724-191">Microsoft Technet</span></span>](http://go.microsoft.com/fwlink/?LinkId=166060)  
  
-   [<span data-ttu-id="25724-192">SMTP サービス (IIS 6.0) の構成</span><span class="sxs-lookup"><span data-stu-id="25724-192">Configuring the SMTP Service (IIS 6.0)</span></span>](http://go.microsoft.com/fwlink/?LinkId=150456)  
  
-   [<span data-ttu-id="25724-193">IIS 7.0: SMTP 電子メールを構成します。</span><span class="sxs-lookup"><span data-stu-id="25724-193">IIS 7.0: Configure SMTP E-Mail</span></span>](http://go.microsoft.com/fwlink/?LinkId=150457)  
  
-   [<span data-ttu-id="25724-194">SMTP サービスをインストールする方法</span><span class="sxs-lookup"><span data-stu-id="25724-194">How to Install the SMTP Service</span></span>](http://go.microsoft.com/fwlink/?LinkId=150458)  
  
 <span data-ttu-id="25724-195">ダウンロードには、サードパーティで提供されている SMTP エミュレーターを使用できます。</span><span class="sxs-lookup"><span data-stu-id="25724-195">SMTP emulators provided by third parties are available for download.</span></span>  
  
##### <a name="to-run-this-sample"></a><span data-ttu-id="25724-196">このサンプルを実行するには</span><span class="sxs-lookup"><span data-stu-id="25724-196">To run this sample</span></span>  
  
1.  <span data-ttu-id="25724-197">[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を使用して、SendMail.sln ソリューション ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="25724-197">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the SendMail.sln solution file.</span></span>  
  
2.  <span data-ttu-id="25724-198">有効な SMTP サーバーへのアクセス権があることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="25724-198">Ensure that you have access to a valid SMTP server.</span></span> <span data-ttu-id="25724-199">セットアップ手順を参照してください。</span><span class="sxs-lookup"><span data-stu-id="25724-199">See the set-up instructions.</span></span>  
  
3.  <span data-ttu-id="25724-200">サーバー アドレスと電子メールの差出人アドレスおよび宛先アドレスを使用してプログラムを構成します。</span><span class="sxs-lookup"><span data-stu-id="25724-200">Configure the program with your server address, and From and To e-mail addresses.</span></span>  
  
     <span data-ttu-id="25724-201">このサンプルを正しく実行するには、電子メールの差出人アドレスおよび宛先アドレスの値と Program.cs および Sequence.xaml の SMTP サーバーのアドレスを設定する必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="25724-201">To correctly run this sample, you may need to configure the value of From and To e-mail addresses and the address of the SMTP server in  Program.cs and in Sequence.xaml.</span></span> <span data-ttu-id="25724-202">プログラムでは電子メールが 2 つの方法で送信されるため、両方の場所でアドレスを変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="25724-202">You will need to change the address in both locations since the program sends mail in two different ways</span></span>  
  
4.  <span data-ttu-id="25724-203">ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。</span><span class="sxs-lookup"><span data-stu-id="25724-203">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
5.  <span data-ttu-id="25724-204">ソリューションを実行するには、Ctrl キーを押しながら F5 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="25724-204">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="25724-205">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="25724-205">The samples may already be installed on your machine.</span></span> <span data-ttu-id="25724-206">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="25724-206">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="25724-207">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="25724-207">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="25724-208">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="25724-208">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\SendMail`
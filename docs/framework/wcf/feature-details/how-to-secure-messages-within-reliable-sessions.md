---
title: "方法 : 信頼できるセッション内でメッセージをセキュリティで保護する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: aee33e50-936f-4486-9ca8-c1520c19a62d
caps.latest.revision: 8
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 8
---
# 方法 : 信頼できるセッション内でメッセージをセキュリティで保護する
ここでは、信頼できるセッション内で交換されるメッセージに対して、メッセージ レベルのセキュリティを有効にするために必要な手順について説明します。このとき、信頼できるセッションがオプションでサポートされているシステム指定のバインディングを使用します。セキュリティで保護された信頼できるセッションを有効にするには、コードを使用して強制的に行うか、構成ファイルで宣言します。この手順では、クライアントとサービスの構成ファイルを使用して、セキュリティで保護された信頼できるセッションを有効にします。  
  
 この手順の主な部分は、次の 3 つの作業で構成されます。  
  
1.  クライアントとサービスのメッセージ交換は信頼できるセッション内で行うことを指定します。  
  
2.  信頼できるセッション内でメッセージ レベルのセキュリティを要求します。  
  
3.  サービスに対する認証時にクライアントが使用する必要があるクライアント資格情報を指定します。  
  
 最初の作業で重要なのは、エンドポイント構成要素に \(この例の場合\) "MessageSecurity" という名前のバインディング構成を参照する `bindingConfiguration` 属性が含まれていることです。[\<binding\>](../../../../docs/framework/misc/binding.md) 構成要素は、この名前を参照して、[reliableSession](http://msdn.microsoft.com/ja-jp/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b) 要素の `enabled` 属性を `true` に設定することで信頼できるセッションを有効にします。信頼できるセッション内で使用できる順序付き配信の保証は、`ordered` 属性を `true` に設定することによって要求できます。  
  
 この構成手順のベースであるソース例については、「[WS 信頼できるセッション](../../../../docs/framework/wcf/samples/ws-reliable-session.md)」を参照してください。  
  
 2 番目の作業で必要な項目は、クライアントとサービスの\<`binding`\> 要素に含まれている \<`security`\> 要素の `mode` 属性を `Message` に設定することによって達成できます。  
  
 3 番目の作業で必要な項目は、クライアントとサービスの\<`security`\> 要素に含まれている \<`message`\> 要素の `clientCredentialType` 属性を `Certificate` に設定することによって達成できます。  
  
> [!NOTE]
>  信頼できるセッションでメッセージ セキュリティを使用するときに、クライアントが認証されていないと、信頼できるメッセージ機能は最初の失敗で例外をスローするのではなく、タイムアウトが発生するまでクライアントの認証を試みます。  
  
### 信頼できるセッションを使用するためにサービスを WSHttpBinding で構成するには  
  
1.  この手順については、「[方法 : 信頼されたセッション内のメッセージを変換する](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md)」を参照してください。  
  
### 信頼できるセッションを使用するためにクライアントを WSHttpBinding で構成するには  
  
1.  この手順については、「[方法 : 信頼されたセッション内のメッセージを変換する](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md)」を参照してください。  
  
### 構成でモードと ClientCredentialType を設定するには  
  
1.  構成ファイルの [\<bindings\>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) 要素に、適切なバインド要素を追加します。次の例では [\<wsHttpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) 要素を追加しています。  
  
2.  \<`binding`\> 要素を追加し、`name` 属性に適切な値を設定します。  
  
3.  `<security>` 要素を追加し、`mode` 属性に `Message` を設定します。  
  
     次の例では、mode を `Message` に設定し、\<`message`\> 要素の `clientCredentialType` 属性を `Certificate` に設定します。  
  
    ```  
    <wsHttpBinding>  
    <binding name="MessageSecurity">  
        <security mode="Message" />  
           <message clientCredentialType = " Certificate" />  
        </security>  
    </binding>  
    </wsHttpBinding >  
    ```
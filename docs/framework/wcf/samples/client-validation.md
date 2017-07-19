---
title: "クライアント検証 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f0c1f805-1a81-4d0d-a112-bf5e2e87a631
caps.latest.revision: 15
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 15
---
# クライアント検証
サービスは頻繁にメタデータを公開し、クライアント プロキシの型を自動的に生成して構成できるようにします。  サービスが信頼できない場合、クライアント アプリケーションでは、セキュリティ、トランザクション、サービス コントラクトの型などに関して、メタデータがクライアント アプリケーションのポリシーに合致しているかどうか検証する必要があります。  次のサンプルでは、サービス エンドポイントを検証するクライアント エンドポイントの動作を記述して、サービス エンドポイントを安全に使用できることを確認する方法を示します。  
  
 サービスは 4 つのサービス エンドポイントを公開します。  1 つ目は WSDualHttpBinding を使用するエンドポイント、2 つ目は NTLM 認証を使用するエンドポイント、3 つ目はトランザクション フローを有効にするエンドポイント、4 つ目は証明書ベースの認証を使用するエンドポイントです。  
  
 クライアントは <xref:System.ServiceModel.Description.MetadataResolver> クラスを使用してサービスのメタデータを取得します。  クライアントは検証動作を使用して、二重バインディング、NTLM 認証、およびトランザクション フローを禁止するポリシーを適用します。  クライアント アプリケーションは、サービスのメタデータからインポートされた <xref:System.ServiceModel.Description.ServiceEndpoint> インスタンスごとに `InternetClientValidatorBehavior` エンドポイント動作のインスタンスを <xref:System.ServiceModel.Description.ServiceEndpoint> に追加し、その後 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] クライアントを使用してエンドポイントへの接続を試行します。  動作の `Validate` メソッドはサービスで操作が呼び出される前に実行され、`InvalidOperationExceptions` をスローすることによってクライアントのポリシーを適用します。  
  
### サンプルをビルドするには  
  
1.  ソリューションをビルドするには、「[Windows Communication Foundation サンプルのビルド](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。  
  
### サンプルを同じコンピューターで実行するには  
  
1.  管理特権を使用して Visual Studio コマンド プロンプトを開き、サンプルのインストール フォルダーから Setup.bat を実行します。  これにより、サンプルの実行に必要なすべての証明書がインストールされます。  
  
2.  サービス アプリケーションを \\service\\bin\\Debug で実行します。  
  
3.  クライアント アプリケーションを \\client\\bin\\Debug で実行します。  クライアント アクティビティがクライアントのコンソール アプリケーションに表示されます。  
  
4.  クライアントとサービス間で通信できない場合は、「[Troubleshooting Tips](http://msdn.microsoft.com/ja-jp/8787c877-5e96-42da-8214-fa737a38f10b)」を参照してください。  
  
5.  サンプルの使用が終わったら、Cleanup.bat を実行して証明書を削除してください。  他のセキュリティ サンプルでも同じ証明書を使用します。  
  
### サンプルを複数のコンピューターで実行するには  
  
1.  サーバー上で、管理特権を使用して Visual Studio コマンド プロンプトを実行し、「`setup.bat service`」と入力します。  `setup.bat` `` に `service` 引数を指定して実行すると、コンピューターの完全修飾ドメイン名を使用してサービス証明書が作成され、Service.cer というファイルにエクスポートされます。  
  
2.  サーバーで、App.config を編集して新しい証明書の名前を反映します。  つまり、[\<serviceCertificate\>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) 要素の `findValue` 属性をコンピューターの完全修飾ドメイン名に変更します。  
  
3.  Service.cer ファイルを、サービス ディレクトリからクライアント コンピューターのクライアント ディレクトリにコピーします。  
  
4.  クライアント上で、管理者特権を使用して Visual Studio コマンド プロンプトを開き、「`setup.bat client`」と入力します。  `setup.bat` `` に `client` 引数を指定して実行すると、Client.com というクライアント証明書が作成され、Client.cer というファイルにエクスポートされます。  
  
5.  client.cs ファイルで、MEX エンドポイントと、既定のサーバー証明書を設定するための `findValue` のアドレス値を、サービスの新しいアドレスに合わせて変更します。  そのためには、localhost をサーバーの完全修飾ドメイン名に置き換えます。  再ビルドします。  
  
6.  Client.cer ファイルを、クライアント ディレクトリからサーバーのサービス ディレクトリにコピーします。  
  
7.  クライアント上で、管理特権を使用して Visual Studio コマンド プロンプトを開き、ImportServiceCert.bat を実行します。  これにより、サービス証明書が Service.cer ファイルから CurrentUser \- TrustedPeople ストアにインポートされます。  
  
8.  サーバー上で、管理特権を使用して Visual Studio コマンド プロンプトを開き、ImportClientCert.bat を実行します。  これにより、クライアント証明書が Client.cer ファイルから LocalMachine \- TrustedPeople ストアにインポートされます。  
  
9. サービス コンピューターの Visual Studio でサービス プロジェクトをビルドし、service.exe を実行します。  
  
10. クライアント コンピューターで、client.exe を実行します。  
  
    1.  クライアントとサービス間で通信できない場合は、「[Troubleshooting Tips](http://msdn.microsoft.com/ja-jp/8787c877-5e96-42da-8214-fa737a38f10b)」を参照してください。  
  
### サンプルの実行後にクリーンアップするには  
  
-   サンプルの実行が終わったら、サンプル フォルダーにある Cleanup.bat を実行します。  
  
    > [!NOTE]
    >  このサンプルを複数のコンピューターで実行している場合、このスクリプトはサービス証明書をクライアントから削除しません。  複数のコンピューターで証明書を使用する [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サンプルを実行した場合は、CurrentUser \- TrustedPeople ストアにインストールされたサービス証明書を忘れずに削除してください。  削除するには、コマンド `certmgr -del -r CurrentUser -s TrustedPeople -c -n <サーバー コンピューターの完全修飾名>`を実行します。たとえば、"certmgr \-del \-r CurrentUser \-s TrustedPeople \-c \-n server1.contoso.com" となります。  
  
## 参照  
 [メタデータを使用する](../../../../docs/framework/wcf/feature-details/using-metadata.md)
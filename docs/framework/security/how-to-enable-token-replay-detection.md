---
title: "方法: トークン再生検出を有効にする | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5a9f5771-f5f6-4100-8501-406aa20d731a
caps.latest.revision: 4
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 4
---
# 方法: トークン再生検出を有効にする
## 対象  
  
-   Microsoft® Windows® の ID Foundation \(WIF\)  
  
-   Web フォーム ASP.NET®  
  
## 概要  
 ここでは、WIF を使用する ASP.NET アプリケーションの再生トークンの検出を有効にする詳細な手順を示します。  また、トークンを再生する手順の検出が有効になっていることを確認するアプリケーションをテストできます。  ここでは、セキュリティ トークン Services \(STS\) を作成するための詳細な手順がない場合、代わりに ID およびアクセス ツールに付属の開発の STS を使用します。  開発の STS は、実際の認証を実行せずにのみテストのために用意されています。  これをどのように実行する ID とアクセス ツールをインストールする必要があります。  これは、次の場所からダウンロードすることもできます: [ID アクセスおよびツール](http://go.microsoft.com/fwlink/?LinkID=245849)  
  
## 内容  
  
-   対象  
  
-   概要  
  
-   手順の概要  
  
-   手順 1 \- 単純な ASP.NET Web フォーム アプリケーションを作成し、再生の検出を有効にします。  
  
-   手順 2 \- ソリューションをテストします。  
  
## 対象  
  
-   ID から WIF および開発の STS を使用して作成し、ツールにアクセスする簡単な ASP.NET アプリケーションを  
  
-   再生トークンの検出を有効にし、動作していることを確認します。  
  
## 概要  
 再生攻撃は、クライアントがクライアントが既に使用している STS のトークンを使用して証明書利用者に認証しようとすると発生します。  この攻撃を防止するために、WIF は既に使用されている STS トークンの再生の検出のキャッシュが含まれます。  有効にすると、再生の検出は、受信した要求のトークンをチェックし、そのトークンが既に使用されているかどうかを確認します。  トークンが既に使用されている場合は、要求は断られ、<xref:System.IdentityModel.Tokens.SecurityTokenReplayDetectedException> 例外がスローされます。  
  
 次の手順では、再生の検出を有効にするために必要な設定を示します。  
  
## 手順の概要  
  
-   手順 1 \- 単純な ASP.NET Web フォーム アプリケーションを作成し、再生の検出を有効にします。  
  
-   手順 2 \- ソリューションをテストします。  
  
## 手順 1 \- 単純な ASP.NET Web フォーム アプリケーションを作成し、再生の検出を有効にします。  
 この手順では、新しい ASP.NET Web フォーム アプリケーションを作成し、再生の検出を有効にするには、*Web.config ファイルを* 変更します。  
  
#### 単純な ASP.NET アプリケーションを作成するには  
  
1.  次に、Visual Studio を起動し、**ファイル**、**新規作成**と **プロジェクト**をクリックします。  
  
2.  **新しいプロジェクト** のペインで、**ASP.NET Web フォーム アプリケーション**をクリックします。  
  
3.  **名前**では、`TestApp` を入力し、**OK**を押します。  
  
4.  **TestApp** のプロジェクトを **ソリューション エクスプローラー**の下にあるを右クリックして、を **Identity and Access**を選択します。  
  
5.  **Identity and Access** のウィンドウが表示されます。  **プロバイダ**の\[ **ローカルの開発用 STS でアプリケーションをテストします。**は、を **適用**をクリックします。  
  
6.  示したのような **\<system.identityModel\>** と **\<identityConfiguration\>** の要素の後に *Web.config 構成ファイル* に **\<tokenReplayDetection\>** の次の要素を追加します:  
  
    ```  
    <system.identityModel>  
        <identityConfiguration>  
            <tokenReplayDetection enabled=”true”/>  
    ```  
  
## 手順 2 \- ソリューションをテストします。  
 この手順では、再生の検出が有効になっていることを検証する、ASP.NET WIF 対応アプリケーションをテストします。  
  
#### 再生の検出の、ASP.NET WIF 対応アプリケーションをテストするには  
  
1.  **F5** キーを押してソリューションを実行します。  既定の ASP.NET のホーム ページという名前で、開発 STS によって返される既定のユーザーであるユーザー名と *テリー*自動的に認証されます。  
  
2.  ブラウザーの **\[戻る\]** のをクリックします。  次の説明を含める **「\/」のサーバー アプリケーション エラー** のページという名前を付ける必要があります: *ID1062: 再生が検出されました: トークン: 'System.IdentityModel.Tokens.SamlSecurityToken'*、*AssertionId* および *発行元が*表示されている。  
  
     トークン再生が検出されたときに型 <xref:System.IdentityModel.Tokens.SecurityTokenReplayDetectedException> の例外がスローされたため、このエラー ページが表示されています。  このエラーは、トークンが最初に指定した場合に、最初の POST 要求を送信し直すしようとしているからです。  **\[戻る\]** のボタンにより、サーバーへの以降の要求でこの動作は発生しません。
---
title: "方法 : サービスのセキュリティ コンテキストを指定する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "コンテキスト, Visual Studio のセキュリティ"
  - "セキュリティ [Visual Studio], コンテキスト"
  - "セキュリティ [Visual Studio], サービス アプリケーション"
  - "ServiceInstaller クラス, セキュリティ コンテキスト"
  - "ServiceProcessInstaller クラス, セキュリティ コンテキスト"
  - "サービス, セキュリティ"
  - "Windows サービス アプリケーション, セキュリティ"
ms.assetid: 02187c7b-dbf2-45f2-96c2-e11010225a22
caps.latest.revision: 10
author: "ghogen"
ms.author: "ghogen"
manager: "douge"
caps.handback.revision: 10
---
# 方法 : サービスのセキュリティ コンテキストを指定する
既定では、サービスは、ログイン ユーザーのセキュリティ コンテキストとは異なるセキュリティ コンテキストで実行されます。  サービスは、`LocalSystem` という既定のシステム アカウントのコンテキストで実行されます。このアカウントがサービスに認可するシステム リソースへのアクセス特権は、ユーザーに認可するものとは異なります。  この動作を変更して、サービスを実行する他のユーザー アカウントを指定できます。  
  
 セキュリティ コンテキストを設定するには、サービスが実行されるプロセスの <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> プロパティを操作します。  このプロパティを使用することにより、サービスを次の 4 種類のアカウントのうちのいずれかに設定できます。  
  
-   `User`。サービスをインストールするときにシステムによって有効なユーザー名とパスワードが要求され、ネットワーク上の 1 人のユーザーによって指定されたアカウントのコンテキストで実行されます。  
  
-   `LocalService`。ローカル コンピューターで非特権ユーザーとして機能するアカウントのコンテキストで実行され、リモート サーバーには匿名の資格情報を渡します。  
  
-   `LocalSystem`は、リモート サーバーに、各種のローカル権限を提供する、コンピューター資格情報を表示したりアカウントのコンテキストで実行;  
  
-   `NetworkService`。ローカル コンピューター上で非特権ユーザーとして機能するアカウントのコンテキストで実行され、リモート サーバーにはコンピューター自体の資格情報を渡します。  
  
 詳細については、<xref:System.ServiceProcess.ServiceAccount> 列挙体の解説を参照してください。  
  
### サービスのセキュリティ コンテキストを指定するには  
  
1.  サービスの作成後、必要なインストーラーを追加します。  詳細については、「[方法 : サービス アプリケーションにインストーラーを追加する](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)」を参照してください。  
  
2.  デザイナーで、`ProjectInstaller` クラスにアクセスし、対象となるサービスのサービス プロセス インストーラーをクリックします。  
  
    > [!NOTE]
    >  いずれのサービス アプリケーションの場合でも、少なくとも 2 つのインストール コンポーネントが `ProjectInstaller` クラスにあります。1 つはプロジェクトのすべてのサービスのプロセスをインストールするコンポーネントで、もう 1 つはアプリケーションに含まれているサービス単位でインストールするコンポーネントです。  この場合は、<xref:System.ServiceProcess.ServiceProcessInstaller> を選択します。  
  
3.  **\[プロパティ\]** ウィンドウで、<xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> を適切な値に設定します。  
  
## 参照  
 [Windows サービス アプリケーションの概要](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)   
 [方法 : サービス アプリケーションにインストーラーを追加する](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)   
 [方法 : Windows サービスを作成する](../../../docs/framework/windows-services/how-to-create-windows-services.md)
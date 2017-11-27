---
title: "方法 : サービスのセキュリティ コンテキストを指定する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Service applications, security
- security [Visual Studio], contexts
- contexts, Visual Studio security
- security [Visual Studio], service applications
- ServiceProcessInstaller class, security context
- services, security
- ServiceInstaller class, security context
ms.assetid: 02187c7b-dbf2-45f2-96c2-e11010225a22
caps.latest.revision: "10"
author: ghogen
ms.author: ghogen
manager: douge
ms.openlocfilehash: 50a9c6ff7f02cda4475aa5390181fa5d410af161
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-specify-the-security-context-for-services"></a>方法 : サービスのセキュリティ コンテキストを指定する
既定では、サービスは、ログイン ユーザーの場合よりも別のセキュリティ コンテキストで実行します。 既定のシステム アカウントのコンテキストで実行するサービスと呼ばれる`LocalSystem`、与えるさまざまなアクセス特権ユーザーのシステム リソースにします。 サービスを実行する別のユーザー アカウントを指定するには、この動作を変更することができます。  
  
 操作することで、セキュリティ コンテキストを設定する、<xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A>サービスが実行されるプロセスのプロパティです。 このプロパティでは、次の 4 つのアカウントの種類のいずれかにサービスを設定することができます。  
  
-   `User`、それが原因で、システム、サービスがインストールされているし、ネットワーク上の 1 人のユーザーによって指定されたアカウントのコンテキストで実行されるとき、有効なユーザー名とパスワードを要求するには  
  
-   `LocalService`、、ローカル コンピューターで非特権ユーザーとして機能し、すべてのリモート サーバーへの匿名の資格情報を表示するアカウントのコンテキストで実行します。  
  
-   `LocalSystem`、広範囲のローカル特権を提供し、すべてのリモート サーバーにコンピューターの資格情報を表示するアカウントのコンテキストで実行します。  
  
-   `NetworkService`、、ローカル コンピューターで非特権ユーザーとしては機能し、リモート サーバーにコンピューターの資格情報を提示するアカウントのコンテキストで実行します。  
  
 詳細については、<xref:System.ServiceProcess.ServiceAccount> 列挙型のページをご覧ください。  
  
### <a name="to-specify-the-security-context-for-a-service"></a>サービスのセキュリティ コンテキストを指定するには  
  
1.  サービスの作成後、必要なインストーラーを追加します。 詳細については、次を参照してください。[する方法: サービス アプリケーションへのインストーラーの追加](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)です。  
  
2.  デザイナーで、アクセス、`ProjectInstaller`クラスを使用しているサービスのサービス プロセスのインストーラーをクリックします。  
  
    > [!NOTE]
    >  少なくとも 2 つのインストール コンポーネントがあるサービス アプリケーションごとに、`ProjectInstaller`クラス: いずれかのプロジェクト、およびアプリケーションを含むサービスごとに 1 つのインストーラーですべてのサービス プロセスをインストールします。 選択すると、このインスタンスで<xref:System.ServiceProcess.ServiceProcessInstaller>です。  
  
3.  **プロパティ**ウィンドウで、設定、<xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A>適切な値にします。  
  
## <a name="see-also"></a>関連項目  
 [Windows サービス アプリケーションの概要](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [方法: サービス アプリケーションへのインストーラーの追加](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)  
 [方法: Windows サービスの作成](../../../docs/framework/windows-services/how-to-create-windows-services.md)

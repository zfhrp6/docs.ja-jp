---
title: "方法 : ASP.NET Web サービス クライアント コードを Windows Communication Foundation に移行する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2e0a22a7-e1d5-4718-8997-4319a7cd9027
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b93460fd6d331b43b49f10cf78fc8863ca1d8d88
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-migrate-aspnet-web-service-client-code-to-the-windows-communication-foundation"></a>方法 : ASP.NET Web サービス クライアント コードを Windows Communication Foundation に移行する
次の手順では、ASP.NET Web サービス クライアント コードを [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] に移行するために従う必要のある大まかな手順を説明します。  
  
## <a name="procedure"></a>プロシージャ  
  
#### <a name="to-migrate-aspnet-web-service-client-code-to-wcf"></a>ASP.NET Web サービス クライアント コードを WCF に移行するには  
  
1.  クライアントの包括的なテスト セットが存在することを確認します。  
  
2.  Visual Studio 2005 を使用して、クライアント アプリケーションを .NET 2.0 にアップグレードします。 テスト セットを実行します。  
  
3.  クライアント プロジェクトから ASP.NET クライアント コードを削除します。 このコードは、WSDL.exe ツールを使用して生成したモジュールにあります。  
  
4.  生成[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]クライアント コードを使用して、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)です。 このコードをクライアント プロジェクトに追加し、構成の出力をクライアントの既存の構成ファイルにマージします。  
  
5.  アプリケーションをコンパイルします。 以前の ASP.NET クライアント型への参照を新しい [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアント型への参照に置き換えることで、コンパイル エラーを修正します。  
  
6.  テスト セットを実行します。  
  
## <a name="see-also"></a>関連項目  
 [方法: ASP.NET Web サービスのコードを Windows Communication Foundation に移行](../../../../docs/framework/wcf/feature-details/migrate-asp-net-web-service-to-wcf.md)

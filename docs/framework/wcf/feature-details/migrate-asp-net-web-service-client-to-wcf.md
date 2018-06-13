---
title: '方法 : ASP.NET Web サービス クライアント コードを Windows Communication Foundation に移行する'
ms.date: 03/30/2017
ms.assetid: 2e0a22a7-e1d5-4718-8997-4319a7cd9027
ms.openlocfilehash: cb60f9cb2e8f35ee703b049eae9e3d99c1ec7d49
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33491131"
---
# <a name="how-to-migrate-aspnet-web-service-client-code-to-the-windows-communication-foundation"></a>方法 : ASP.NET Web サービス クライアント コードを Windows Communication Foundation に移行する
次の手順では、ASP.NET Web サービス クライアント コードを WCF に移行後にする必要のある大まかな手順について説明します。  
  
## <a name="procedure"></a>プロシージャ  
  
#### <a name="to-migrate-aspnet-web-service-client-code-to-wcf"></a>ASP.NET Web サービス クライアント コードを WCF に移行するには  
  
1.  クライアントの包括的なテスト セットが存在することを確認します。  
  
2.  Visual Studio 2005 を使用して、クライアント アプリケーションを .NET 2.0 にアップグレードします。 テスト セットを実行します。  
  
3.  クライアント プロジェクトから ASP.NET クライアント コードを削除します。 このコードは、WSDL.exe ツールを使用して生成したモジュールにあります。  
  
4.  WCF クライアントを使用してコードを生成、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)です。 このコードをクライアント プロジェクトに追加し、構成の出力をクライアントの既存の構成ファイルにマージします。  
  
5.  アプリケーションをコンパイルします。 新しい WCF クライアント型への参照を以前の ASP.NET クライアント型への参照を置き換えることで、コンパイル エラーを修復します。  
  
6.  テスト セットを実行します。  
  
## <a name="see-also"></a>関連項目  
 [方法 : ASP.NET Web サービス コードを Windows Communication Foundation に移行する](../../../../docs/framework/wcf/feature-details/migrate-asp-net-web-service-to-wcf.md)

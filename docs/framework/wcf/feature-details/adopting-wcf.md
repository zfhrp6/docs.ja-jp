---
title: Windows Communication Foundation の採用
ms.date: 03/30/2017
ms.assetid: 49ba71e2-9468-4082-84c5-cf8daf95e34a
ms.openlocfilehash: bcd6543e6cd47dc723b308acebec6f492fa14fb1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="adopting-windows-communication-foundation"></a>Windows Communication Foundation の採用
ASP.NET を使用して既存のアプリケーションのメンテナンスを続行開発中に、新しい開発では、Windows Communication Foundation (WCF) を使用するメッセージが表示できます。 WCF は、どのようなシナリオでの .NET Framework でビルドされたアプリケーションとの通信を促進するための最適な選択をするものでは、ためとして機能できるさまざまな方法でソフトウェア通信の問題を解決するための標準ツールを ASP.NETできません。  
  
 新しい WCF アプリケーションは、既存の ASP.NET Web サービスと同じコンピューターに展開できます。 既存の ASP.NET Web サービスは、.NET Framework バージョン 2.0 より前のバージョンを使用する場合は、選択的に IIS アプリケーションを新しい WCF アプリケーションをホストするのには .NET Framework 2.0 を展開する、ASP.NET IIS 登録ツールを使用できます。 そのツールについては、 [ASP.NET IIS 登録ツール (Aspnet_regiis.exe)](http://go.microsoft.com/fwlink/?LinkId=94687)、ユーザー インターフェイスは、IIS 6.0 管理コンソールに組み込まれているとします。  
  
 WCF サービスが IIS で既存の ASP.NET Web サービス アプリケーションを ASP.NET 互換モードで実行するように構成を追加して既存の ASP.NET Web サービスに新機能を追加する、WCF を使用できます。 新しい WCF サービスのコードにアクセスしを使用して、既存の ASP.NET コードと同じアプリケーションの状態情報を更新する ASP.NET 互換モードにより、<xref:System.Web.HttpContext>クラスです。 また、アプリケーションは同じクラス ライブラリを共有することもできます。  
  
 WCF クライアントは、ASP.NET Web サービスを使用できます。 WCF サービスで構成されている、 <xref:System.ServiceModel.BasicHttpBinding> ASP.NET Web サービス クライアントで使用されることができます。 ASP.NET Web サービスは、WCF アプリケーションと共存させることができ、WCF を使用して既存の ASP.NET Web サービスに機能を追加することもできます。 WCF と ASP.NET Web サービスを組み合わせて使用する次の方法を考えると、WCF と ASP.NET Web いないサービスによって提供される機能を必要とする場合にのみ、ASP.NET Web サービスを WCF に移行することがあります。  
  
 このような移行が必要となるまれな場合においても、あるテクノロジから別のテクノロジへコードを移行するのは、ほとんどの場合、正しいアプローチではないということを考慮する必要があります。 以前のテクノロジでは満たされない新しい要件を満たすために新しいテクノロジを採用する場合、新たに拡張された要件を満たす新しいソリューションを設計することが正しい方法です。 新しい設計では、既存のシステムでの経験とそのシステムを設計して以来、獲得した知識を活用できます。 また、新しい設計は、新しいプラットフォーム上で古い設計を再制作するのではなく、新しいテクノロジの機能を十分に活用することができます。 新しい設計の主要な要素のプロトタイプが完成すると、既存のシステムのコードを新しいシステム内で再使用することが容易になります。  
  
 まれな場合の ASP.NET Web サービスから WCF への移植では、適切なソリューションには、次のセクションでは続行する方法のガイダンスを提供します。 これには、サービスを移行する方法、およびクライアントを移行する方法についてのアドバイスが含まれています。  
  
 既存の ASP.NET Web サービスを WCF に移行する方法の完全な分析を参照してください[ASP.NET Web サービスおよび Windows Communication Foundation](http://go.microsoft.com/fwlink/?LinkID=71761)です。 このセクションでは、ASP.NET Web サービスのメタデータから WCF 準拠サービスを実装する方法と ASP.NET Web サービスとクライアントのコードを WCF に移行する方法について説明します。  
  
## <a name="see-also"></a>関連項目  
 [方法 : メタデータの取得および準拠サービスの実装をする](../../../../docs/framework/wcf/feature-details/how-to-retrieve-metadata-and-implement-a-compliant-service.md)  
 [方法 : ASP.NET Web サービス コードを Windows Communication Foundation に移行する](../../../../docs/framework/wcf/feature-details/migrate-asp-net-web-service-to-wcf.md)  
 [方法 : ASP.NET Web サービス クライアント コードを Windows Communication Foundation に移行する](../../../../docs/framework/wcf/feature-details/migrate-asp-net-web-service-client-to-wcf.md)

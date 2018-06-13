---
title: ASP.NET Web サービスを WCF に移行する
ms.date: 03/30/2017
ms.assetid: 1adbb931-f0b1-47f3-9caf-169e4edc9907
ms.openlocfilehash: 7d43c66952d17a91e38ae1b086478b9416321b8a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33494563"
---
# <a name="migrating-aspnet-web-services-to-wcf"></a>ASP.NET Web サービスを WCF に移行する
ASP.NET には Web サービスを構築するための .NET Framework クラス ライブラリとツールが用意されています。また、インターネット インフォメーション サービス (IIS) 内でサービスをホストする機能も用意されています。 Windows Communication Foundation (WCF) では、.NET Framework クラス ライブラリ、ツール、および Web サービスで使用されるものを含む、任意のプロトコルを使用して通信するソフトウェア エンティティを有効にするためのホスティング機能を提供します。  WCF に移行する ASP.NET Web サービスは、新しい機能と WCF に固有の機能強化を活用するために、アプリケーションを許可します。  
  
 WCF では、ASP.NET Web サービスと比較したいくつかの重要な利点がします。 ASP.NET Web サービスのツールは、Web サービスを構築するためだけですが、WCF には、ソフトウェア エンティティが相互に通信するために行う必要があるときに使用できるツールが用意されています。 これにより、さまざまなソフトウェア通信シナリオを実現するために開発者が知っておく必要があるテクノロジの数が少なくて済むため、ソフトウェア開発プロジェクトが完了するまでの時間だけでなく、ソフトウェア開発リソースのコストが削減されます。  
  
 Web サービスの開発プロジェクトにでもは、WCF は、ASP.NET Web サービスのサポートよりも多くの Web サービス プロトコルをサポートします。 これらの追加プロトコルにより、特に信頼できるセッションとトランザクションという点で、より洗練されたソリューションが実現されます。  
  
 WCF では、ASP.NET Web サービスよりもメッセージの転送を複数のプロトコルをサポートしています。 ASP.NET Web サービスでは、HTTP (ハイパーテキスト転送プロトコル) を使用したメッセージの送信しかサポートしていません。 WCF では、HTTP、だけでなく、伝送制御プロトコル (TCP)、名前付きパイプ、および Microsoft メッセージ キュー (MSMQ) を使用して、メッセージの送信をサポートしています。 重要な WCF は追加のトランスポート プロトコルをサポートするために拡張できます。 したがって、WCF を使用して開発されたソフトウェアは多様によって潜在的な投資収益率を高める、他のソフトウェアと連携するように調整できます。  
  
 WCF を展開するための豊富な程度機能が用意されていて、ASP.NET Web サービスよりも、アプリケーションの管理を提供します。 構成エディターを提供する WCF ASP.NET には、また、構成システムに加えて送信者から受信側と任意の数の中継ぎ局、トレース ビューアー、メッセージ ログ、多数のパフォーマンス カウンターを介したへのアクティビティ トレースとWindows Management Instrumentation のサポート。  
  
 を使用しているか、いくつかのオプションがある ASP.NET Web サービスの使用を検討している場合サービス、ASP.NET Web 相対 WCF のこれらの潜在的メリットを指定します。  
  
-   ASP.NET Web サービスを使用し、WCF によって提供される利点をしないに進みます。  
  
-   いずれかの時点が後で WCF を採用する目的で ASP.NET Web サービスの使用を継続します。 このセクションのトピックでは、将来の WCF アプリケーションと共に新しい ASP.NET Web サービス アプリケーションを使用するための導入を最大化する方法を説明します。 このセクションのトピックでは、新しい ASP.NET Web WCF に移行しやすくためにサービスを構築する方法についても説明します。 ただし、サービスのセキュリティ保護することは重要で、信頼性やトランザクションの保証が必要ですが場合、またはカスタムの管理機能が、構築する必要があるし、WCF を採用することをお勧めします。 WCF は、このようなシナリオでは正確に適しています。  
  
-   既存の ASP.NET Web サービス アプリケーションを維持しながら新しい開発では、WCF を採用します。 おそらくこれが最適な選択です。 使用する既存のアプリケーションを変更した場合のコストを引き出しつつ、WCF の利点が得られます。 このシナリオでは新しい WCF アプリケーションと共存できます既存の ASP.NET アプリケーション。 新しい WCF アプリケーションが既存の ASP.NET Web サービスを使用できなくなり、WCF は、WCF の ASP.NET 互換モードにより、既存の ASP.NET アプリケーションに新しい処理機能をプログラミングするために使用できます。  
  
-   WCF を採用し、既存の ASP.NET Web サービス アプリケーションを WCF に移行します。 このオプションは、WCF によって提供される機能と既存のアプリケーションを強化するためにや新しい内の既存の ASP.NET Web サービスの機能より強力な WCF アプリケーションを再現することもできます。  
  
> [!NOTE]
>  注意する必要がある場合は、WCF サービスをホストして IIS 5.x と ASP.NET がアンインストールされます。 WCF サービスが IIS によってホストされると ASP.NET がアンインストールされている場合は、5.x では、サービスのコードを要求することができます。 IIS を実行しているオペレーティング システムで ASP.NET がアンインストール 5.x と WCF がアンインストールされる、拡張子 .svc を持つファイルはテキスト ファイルと見なさ、ソース コードを含む、内容が、要求元に返されます。  
  
 このセクションでは、これらのオプションの詳細について説明します、WCF を ASP.NET Web サービスを比較し、ASP.NET Web サービス コードを WCF に移行する方法について説明します。  
  
## <a name="see-also"></a>関連項目  
 [Windows Communication Foundation の採用: 将来の移行の簡略化](../../../../docs/framework/wcf/feature-details/anticipating-adopting-wcf-migration.md)  
 [Windows Communication Foundation 導入の準備: 将来的な統合の容易化](../../../../docs/framework/wcf/feature-details/anticipating-adopting-the-wcf-easing-future-integration.md)  
 [Windows Communication Foundation の採用](../../../../docs/framework/wcf/feature-details/adopting-wcf.md)  
 [使用目的と使用標準に基づく ASP.NET Web サービスと WCF との比較](../../../../docs/framework/wcf/feature-details/comparing-aspnet-web-services-to-wcf-based-on-purpose-and-standards-used.md)  
 [開発者の視点から見た ASP.NET Web サービスと WCF との比較](../../../../docs/framework/wcf/feature-details/comparing-aspnet-web-services-to-wcf-based-on-development.md)

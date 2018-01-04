---
title: "ASP.NET Web サービスを WCF に移行する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1adbb931-f0b1-47f3-9caf-169e4edc9907
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f90f7dd508e2ff4058b787fc29d152abc18f24fd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="migrating-aspnet-web-services-to-wcf"></a>ASP.NET Web サービスを WCF に移行する
ASP.NET には Web サービスを構築するための .NET Framework クラス ライブラリとツールが用意されています。また、インターネット インフォメーション サービス (IIS) 内でサービスをホストする機能も用意されています。 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] には、.NET Framework クラス ライブラリ、ツール、およびホスティング機能が用意されており、ソフトウェア エンティティが、Web サービスによって使用されるプロトコルを含む、任意のプロトコルを使用して通信できるようになっています。  ASP.NET Web サービスから [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] に移行すると、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 独自の新しい機能や強化された機能をアプリケーションで利用できます。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] には、ASP.NET Web サービスと比較した場合に重要な利点がいくつかあります。 ASP.NET Web サービスのツールは Web サービスの構築専用であるのに対して、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] が提供するツールは、ソフトウェア エンティティを互いに通信させる必要がある場合にも使用できます。 これにより、さまざまなソフトウェア通信シナリオを実現するために開発者が知っておく必要があるテクノロジの数が少なくて済むため、ソフトウェア開発プロジェクトが完了するまでの時間だけでなく、ソフトウェア開発リソースのコストが削減されます。  
  
 Web サービスの開発プロジェクトの場合でも、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は ASP.NET Web サービスよりも多くの Web サービス プロトコルをサポートします。 これらの追加プロトコルにより、特に信頼できるセッションとトランザクションという点で、より洗練されたソリューションが実現されます。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では ASP.NET Web サービスに比べ、多くのメッセージ トランスポート用プロトコルをサポートします。 ASP.NET Web サービスでは、HTTP (ハイパーテキスト転送プロトコル) を使用したメッセージの送信しかサポートしていません。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では、HTTP を使用したメッセージの送信のほかに、TCP (伝送制御プロトコル)、名前付きパイプ、MSMQ (Microsoft メッセージ キュー) をサポートしています。 さらに重要なことは、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] を拡張することにより、追加のトランスポート プロトコルをサポートできることです。 これにより、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] を使用して開発されたソフトウェアは、他の多様なソフトウェアと連携するよう適合させることができるため、投資収益率を高めることができます。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では、ASP.NET Web サービスに比べ、アプリケーションを展開および管理するための機能が格段に豊富に提供されています。 ASP.NET でも用意されている構成システムに加えて、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では構成エディター、任意の数の中継局を介した送信者から受信者へのアクティビティ トレース、トレース ビューアー、メッセージ ログ、多数のパフォーマンス カウンター、Windows Management Instrumentation のサポートなどが用意されています。  
  
 ASP.NET Web サービスと比較したときの [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の潜在的な利点を考えると、ASP.NET Web サービスを使用している、または使用を検討している場合、次のようなオプションがあります。  
  
-   ASP.NET Web サービスの使用を継続し、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] で提供される利点については見送ります。  
  
-   将来的には [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] を採用することを見据えながら、ASP.NET Web サービスの使用を継続します。 このセクションのトピックでは、新規作成する ASP.NET Web サービス アプリケーションと将来の [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] アプリケーションとを同時に使用できる可能性を最大限にする方法について説明します。 また、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] への移行を容易にするための、新規の ASP.NET Web サービスの構築方法についても説明します。 ただし、サービスのセキュリティ保護が重要な場合、信頼性やトランザクションの確実性が求められる場合、またはカスタムの管理機能を構築する必要がある場合は、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の採用をお勧めします。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、まさにこのようなシナリオのために設計されています。  
  
-   新規開発については [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] を採用し、既存の ASP.NET Web サービス アプリケーションは保持します。 おそらくこれが最適な選択です。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の利点を引き出しつつ、既存のアプリケーションを変更して WCF を使用できるようにするためのコストを削減できます。 このシナリオでは、新規の [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] アプリケーションは、既存の ASP.NET アプリケーションと共存できます。 新規の [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] アプリケーションは既存の ASP.NET Web サービスを使用でき、また [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] には ASP.NET 互換モードがあるため、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] を使用して既存の ASP.NET アプリケーションに新しい処理機能をプログラムできます。  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] を採用し、既存の ASP.NET Web サービス アプリケーションを [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] に移行します。 このオプションは、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] が提供する機能を使用して既存のアプリケーションを拡張する場合、または既存の ASP.NET Web サービスの機能を新しく、より強力な [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] アプリケーションによって作り直す場合に選択します。  
  
> [!NOTE]
>  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスが IIS 5.x によってホストされており、ASP.NET がアンインストールされている場合は注意が必要です。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスが IIS 5.x によってホストされていて、ASP.NET がアンインストールされている場合、サービスのコードが要求されることがあります。 IIS 5.x が実行されているオペレーティング システムで ASP.NET がアンインストールされており、さらに [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] がアンインストールされると、拡張子 .svc を持つファイルがテキスト ファイルと見なされ、これに含まれる、ソース コードを含む内容は要求元に返されます。  
  
 このセクションでは、上記のオプションの詳細、ASP.NET Web サービスと [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] との比較、ASP.NET Web サービスのコードを [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] に移行する方法の手順について説明します。  
  
## <a name="see-also"></a>参照  
 [Windows Communication Foundation の採用: 将来の移行の簡略化](../../../../docs/framework/wcf/feature-details/anticipating-adopting-wcf-migration.md)  
 [Windows Communication Foundation 導入の準備: 将来的な統合の容易化](../../../../docs/framework/wcf/feature-details/anticipating-adopting-the-wcf-easing-future-integration.md)  
 [Windows Communication Foundation の採用](../../../../docs/framework/wcf/feature-details/adopting-wcf.md)  
 [使用目的と使用標準に基づく ASP.NET Web サービスと WCF との比較](../../../../docs/framework/wcf/feature-details/comparing-aspnet-web-services-to-wcf-based-on-purpose-and-standards-used.md)  
 [開発者の視点から見た ASP.NET Web サービスと WCF との比較](../../../../docs/framework/wcf/feature-details/comparing-aspnet-web-services-to-wcf-based-on-development.md)

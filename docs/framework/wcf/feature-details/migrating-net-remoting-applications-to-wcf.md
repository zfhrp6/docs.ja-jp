---
title: .NET リモート処理アプリケーションの WCF への移行
ms.date: 03/30/2017
helpviewer_keywords:
- ',NET remoting [WCF]'
ms.assetid: 24793465-65ae-4308-8c12-dce4fd12a583
ms.openlocfilehash: 53f63352503a48ee849580e676b5fe98f3dcf2cd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="migrating-net-remoting-applications-to-wcf"></a>.NET リモート処理アプリケーションの WCF への移行
**このトピックの対象は、既存のアプリケーションとの下位互換性のために残されているレガシ テクノロジに特定されています。新規の開発には、このトピックを適用しないでください。WCF を使用して、分散アプリケーションを開発する必要がありますようになりました。**  
  
 既存の .NET リモート処理アプリケーションで WCF を活用するために 2 つの方法: 統合と移行します。 統合を使用すると、.net Remoting 2.0 とを実行している WCF 側の側では、によって、既存の .Net を変更しなくても同時に両方のテクノロジで、同じビジネス オブジェクトを公開すること Remoting 2.0 コード。 統合では、[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 2.0 以降が実行されている必要があります。 WCF の機能を利用して、Remoting 2.0 システムとの互換性をネットワーク上の必要はない場合、は、サービス全体を WCF に移行できます。 .NET Remoting 2.0 から WCF への移行には、リモート オブジェクトのインターフェイスとその構成設定の変更が必要です。 これらのトピックの両方については、「[からリモート処理を Windows Communication Foundation](http://go.microsoft.com/fwlink/?LinkId=74403)です。  
  
## <a name="see-also"></a>関連項目  
 [概念](../../../../docs/framework/wcf/conceptual-overview.md)

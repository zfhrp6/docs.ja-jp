---
title: "Windows Communication Foundation のトランザクションの概要"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- transactions [WCF]
- WCF, transactions
- Windows Communication Foundation, transactions
ms.assetid: c7757854-1207-4019-8b31-552578b7d570
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6fb90d0f93e9bdf7dd9779ffd5d4b1288ba56e7a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="windows-communication-foundation-transactions-overview"></a>Windows Communication Foundation のトランザクションの概要
トランザクションを使用すると、一連の処理や操作を 1 つの不可分の実行単位にグループ化できます。 トランザクションとは、次の性質を持つ操作のコレクションです。  
  
-   原子性。 特定のトランザクションの下で完了したすべての更新は、コミットされて永続的に格納されるか、すべて中止されて前の状態にロールバックされるかのどちらかになります。  
  
-   一貫性。 トランザクション下で行う変更は、一貫性のある状態から別の一貫性のある状態への変換を表します。 たとえば、当座預金から普通預金への振り替えトランザクションでは、全体の預金残高は変更されません。  
  
-   分離 トランザクションが他の同時実行されているトランザクションに属するコミットされていない変更を監視することがなくなります。 分離により、同時実行の抽象概念が提供され、1 つのトランザクションが別のトランザクションの実行に予期しない影響を与える可能性がなくなります。  
  
-   持続性。 マネージ リソース (データベース レコードなど) に対して 1 度コミットされた更新は、障害に直面しても永続的に残ります。  
  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] は、Web サービスアプリケーション内で分散トランザクションを作成できる一連の豊富な機能を提供します。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、WS-AtomicTransaction (WS-AT) プロトコル サポートを実装します。このプロトコルにより [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] アプリケーションは、サードパーティ技術を使って作成された相互運用可能な Web サービスなど、相互運用可能アプリケーションにトランザクションをフローすることができます。 また、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、OLE トランザクション プロトコル サポートも実装します。このプロトコルは、トランザクションのフローを有効にする相互運用可能な機能が必要とされないシナリオで使用することができます。  
  
 アプリケーション構成ファイルを使用してバインディングを構成し、トランザクション フローを有効にしたり無効にしたりできます。また、バインディングに目的のトランザクション プロトコルを設定できます。 さらに、構成ファイルを使用してサービス レベルでのトランザクションのタイムアウトを設定できます。 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][トランザクション フローを有効にする](../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md)です。  
  
 <xref:System.ServiceModel> 名前空間のトランザクション属性で次の設定が行えます。  
  
-   <xref:System.ServiceModel.ServiceBehaviorAttribute> 属性を使用して、トランザクションのタイムアウトと分離レベルのフィルター処理を構成する。  
  
-   <xref:System.ServiceModel.OperationBehaviorAttribute> 属性を使用して、トランザクション機能を有効にし、トランザクションの完了動作を構成する。  
  
-   コントラクト メソッドで <xref:System.ServiceModel.ServiceContractAttribute> 属性と <xref:System.ServiceModel.OperationContractAttribute> 属性を使用して、トランザクション フローの要求、許可、または拒否を行う。  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][ServiceModel トランザクションの属性](../../../../docs/framework/wcf/feature-details/servicemodel-transaction-attributes.md)です。  
  
## <a name="see-also"></a>参照  
 [ServiceModel トランザクションの属性](../../../../docs/framework/wcf/feature-details/servicemodel-transaction-attributes.md)  
 [トランザクション フローの有効化](../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md)

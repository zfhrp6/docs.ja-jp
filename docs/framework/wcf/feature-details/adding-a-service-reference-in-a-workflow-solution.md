---
title: "ワークフロー ソリューションでのサービス参照の追加"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 83574cf3-9803-49bc-837f-432936dc9c76
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 511ff8fa982e9a9ca29faf714725626f7925f659
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="adding-a-service-reference-in-a-workflow-solution"></a>ワークフロー ソリューションでのサービス参照の追加
ワークフロー アプリケーションでのサービス参照の追加は、通常の WCF アプリケーションとは動作が少し異なります。 [サービス参照の追加] を選択し、サービスの URL を指定すると、メタデータがダウンロードされ、カスタム アクティビティが生成されて、参照を追加した WCF サービスまたは WCF ワークフロー サービスを呼び出すことができるようになります。 サービス参照を追加した後、生成されたアクティビティがビルドされるように、ソリューションを再ビルドします。 これにより、アクティビティがワークフロー デザイナー ツールボックスに表示されます。 ただし、この方法が機能するのはワークフロー ソリューション内でサービス参照を追加する場合だけであることに注意してください。 次の web キャストは、その他の種類のプロジェクトでサービス参照を追加する方法を示します: [Web プロジェクトでワークフローから WCF サービスを呼び出す](http://go.microsoft.com/fwlink/?LinkId=207725)です。  
  
 同じ操作名が含まれるサービスへのサービス参照を複数追加すると、問題が発生します。 生成されたアクティビティは最初のサービス操作しか呼び出しません。 この問題を回避するには、サービス操作を別々の名前に変更するか、生成された各アクティビティ内でエンドポイント構成名を変更します。  
  
## <a name="see-also"></a>関連項目  
 [ワークフロー サービス](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [方法: 別のワークフロー サービスを呼び出すワークフロー サービスの作成](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-that-calls-another-workflow-service.md)  
 [Web プロジェクトでワークフローから WCF サービスの呼び出し](http://go.microsoft.com/fwlink/?LinkId=207725)

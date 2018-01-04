---
title: "カスタム アクティビティの使用"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8f356419-681a-4175-ae93-878eee970249
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7558ca965af6cc9acd35ecab47bf9f66f592b15f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="using-a-custom-activity"></a>カスタム アクティビティの使用
<xref:System.Activities.Activity> またはそのサブクラスから派生するアクティビティは、結合してより大規模なワークフローにしたり、コードで直接作成したりすることができます。 このトピックでは、コードまたはデザイナーで作成したワークフロー内でカスタム アクティビティを使用する方法について説明します。  
  
> [!NOTE]
>  カスタム アクティビティとそれを使用するアクティビティの両方のコンパイル (ビルド処理によって生成された、インスタンス化する型では読み込まなど) 限り、それらが定義されている、同じプロジェクトでカスタム アクティビティを使用できます、参照元のアクティビティが読み込まれている場合動的に別のプロジェクトに参照アセンブリを配置する必要がありますし (例: ActivityXAMLServices の使用など)、またはデザイナーで生成される XAML を手作業で編集を有効にする必要があります。  
  
#### <a name="using-a-custom-activity-to-a-workflow-project"></a>ワークフロー プロジェクトへのカスタム アクティビティの使用  
  
1.  ホスト プロジェクトから、カスタム アクティビティを含むアクティビティ ライブラリ プロジェクトへの参照を追加します。  
  
2.  ソリューションをビルドします。  
  
3.  デザイナーでカスタム アクティビティを使用するには、ツールボックスでカスタム アクティビティを探して、そのアクティビティをデザイナー画面にドラッグします。  
  
4.  コード内でカスタム アクティビティを使用するには、カスタム アクティビティ プロジェクトを参照する Using ステートメントを追加し、そのアクティビティの新しいインスタンスを <xref:System.Activities.WorkflowInvoker.Invoke%2A> に渡します。

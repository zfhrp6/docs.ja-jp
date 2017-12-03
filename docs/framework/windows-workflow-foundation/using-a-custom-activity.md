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
ms.openlocfilehash: cea0e819c79550b27a71957f6d8c2c9badfef7c0
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
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

---
title: アクティビティ検証の構成
ms.date: 03/30/2017
ms.assetid: 25a4eccb-b8fc-4857-a01d-2683b6341219
ms.openlocfilehash: e6fa043e0a0a96875319d556c19ab8ee90cd2139
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33512601"
---
# <a name="configuring-activity-validation"></a>アクティビティ検証の構成
アクティビティの検証を使用すると、アクティビティの作成者とユーザーは、アクティビティを実行する前に、アクティビティの構成エラーを特定および報告できます。 Windows Workflow Foundation (WF) は、次の 3 種類のアクティビティの検証を提供します。  
  
-   `RequiredArgument` 属性および `OverloadGroup` 属性。  
  
-   命令型コードに基づく検証。  
  
-   宣言の制約。  
  
 `RequiredArgument` 属性と `OverloadGroup` 属性は、アクティビティにおける特定の引数が必須であることを示します。 命令型コードに基づく検証には、アクティビティが自身に関する検証を提供できる単純な方法が用意されています。また、宣言の制約を使用すると、アクティビティとそれを含むワークフローとの関係に関して検証できます。 検証の要件に従ってアクティビティが正しく構成されていない場合、検証のエラーと警告が返されます。 包含するワークフローをワークフロー デザイナーを使用して作成する場合、デザイナーには任意の検証のエラーと警告が表示されます。 ワークフローをワークフロー デザイナーを使用せずに作成する場合、ワークフローを呼び出すときに任意の検証エラーが返されます。 ワークフローの作成方法にかかわらず、検証エラーを含むワークフローは実行できません。 ここでは、このようなアクティビティの検証に関する概要と、アクティビティの検証を呼び出す方法について説明します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [必須の引数とオーバーロード グループ](../../../docs/framework/windows-workflow-foundation/required-arguments-and-overload-groups.md)  
 検証を実現するために、`RequiredArgument` 属性および `OverloadGroup` 属性を使用する方法について説明します。  
  
 [命令型コードに基づく検証](../../../docs/framework/windows-workflow-foundation/imperative-code-based-validation.md)  
 <xref:System.Activities.CodeActivity> および <xref:System.Activities.NativeActivity> に基づくアクティビティにコードに基づく検証を使用する方法について説明します。  
  
 [宣言の制約](../../../docs/framework/windows-workflow-foundation/declarative-constraints.md)  
 複雑なアクティビティの検証を実現するために宣言の制約を使用する方法について説明します。  
  
 [アクティビティ検証の呼び出し](../../../docs/framework/windows-workflow-foundation/invoking-activity-validation.md)  
 アクティビティの検証が自動的に呼び出される場合と、明示的に検証を呼び出す方法について説明します。  
  
## <a name="reference"></a>参照  
  
## <a name="related-sections"></a>関連項目

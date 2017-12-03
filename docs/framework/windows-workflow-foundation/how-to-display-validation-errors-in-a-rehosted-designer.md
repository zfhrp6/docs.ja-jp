---
title: "方法: 再ホストされたデザイナーの検証エラーを表示する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5aa8fb53-8f75-433b-bc06-7c7d33583d5d
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b9f76f1ad5282ecf10a3ce58db0f6e1bd8df1b4d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-display-validation-errors-in-a-rehosted-designer"></a><span data-ttu-id="476f4-102">方法: 再ホストされたデザイナーの検証エラーを表示する</span><span class="sxs-lookup"><span data-stu-id="476f4-102">How to: Display Validation Errors in a Rehosted Designer</span></span>
<span data-ttu-id="476f4-103">このトピックでは、再ホストされた [!INCLUDE[wfd1](../../../includes/wfd1-md.md)]で検証エラーを取得および発行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="476f4-103">This topic describes how to retrieve and publish validation errors in a rehosted [!INCLUDE[wfd1](../../../includes/wfd1-md.md)].</span></span> <span data-ttu-id="476f4-104">再ホストされたデザイナー内のワークフローが有効であることを確認するために手順を示します。</span><span class="sxs-lookup"><span data-stu-id="476f4-104">This provides us with a procedure to confirm that a workflow in a rehosted designer is valid.</span></span>  
  
 <span data-ttu-id="476f4-105">このタスクは 2 つの部分で構成されています。</span><span class="sxs-lookup"><span data-stu-id="476f4-105">This task has two parts.</span></span> <span data-ttu-id="476f4-106">最初に、<xref:System.Activities.Presentation.Validation.IValidationErrorService> を実装します。</span><span class="sxs-lookup"><span data-stu-id="476f4-106">The first is to provide an implementation <xref:System.Activities.Presentation.Validation.IValidationErrorService>.</span></span>  <span data-ttu-id="476f4-107">このインターフェイスには、1 つの重要なメソッド <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A> を実装します。このメソッドは、エラーに関する情報を含む <xref:System.Activities.Presentation.Validation.ValidationErrorInfo> オブジェクトの一覧をデバッグ ログに渡します。</span><span class="sxs-lookup"><span data-stu-id="476f4-107">There is one critical method to implement on this interface, <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A> which will pass you a list of <xref:System.Activities.Presentation.Validation.ValidationErrorInfo> objects containing information about the errors to the debug log.</span></span>  <span data-ttu-id="476f4-108">このインターフェイスを実装した後に、その実装のインスタンスを編集コンテキストに発行して、エラー情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="476f4-108">After implementing the interface, you retrieve the error information by publishing an instance of that implementation to the editing context.</span></span>  
  
### <a name="implement-the-ivalidationerrorservice-interface"></a><span data-ttu-id="476f4-109">IValidationErrorService インターフェイスの実装</span><span class="sxs-lookup"><span data-stu-id="476f4-109">Implement the IValidationErrorService Interface</span></span>  
  
1.  <span data-ttu-id="476f4-110">以下に、検証エラーをデバッグ ログに書き込む単純な実装を表すコード例を示します。</span><span class="sxs-lookup"><span data-stu-id="476f4-110">Here is a code sample for a simple implementation that will write out the validation errors to the debug log.</span></span>  
  
    ```  
    using System.Activities.Presentation.Validation;  
    using System.Collections.Generic;  
    using System.Diagnostics;  
    using System.Linq;  
  
    namespace VariableFinderShell  
    {  
        class DebugValidationErrorService : IValidationErrorService  
        {  
            public void ShowValidationErrors(IList<ValidationErrorInfo> errors)  
            {  
                errors.ToList().ForEach(vei => Debug.WriteLine(string.Format("Error: {0} ", vei.Message)));  
            }  
        }  
    }  
    ```  
  
### <a name="publishing-to-the-editing-context"></a><span data-ttu-id="476f4-111">編集コンテキストへの発行</span><span class="sxs-lookup"><span data-stu-id="476f4-111">Publishing to the Editing Context</span></span>  
  
1.  <span data-ttu-id="476f4-112">以下に、編集コンテキストに発行するコードを示します。</span><span class="sxs-lookup"><span data-stu-id="476f4-112">Here is the code that will publish this to the editing context.</span></span>  
  
    ```  
    wd.Context.Services.Publish<IValidationErrorService>(new DebugValidationErrorService());  
    ```

---
title: "スタートアップ フォームが指定されていない |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrAppModel_NoStartupForm
dev_langs:
- VB
ms.assetid: 8e04af49-4bef-49de-a7ec-e407e9873da7
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 37484a00a631577e80853822fff92b069dbad7f2
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="a-startup-form-has-not-been-specified"></a><span data-ttu-id="04e3f-102">スタートアップ フォームが指定されていません。</span><span class="sxs-lookup"><span data-stu-id="04e3f-102">A startup form has not been specified</span></span>
<span data-ttu-id="04e3f-103">アプリケーションを使用して、<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>クラスしますが、スタートアップ フォームを指定していません</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>。</span><span class="sxs-lookup"><span data-stu-id="04e3f-103">The application uses the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> class but does not specify the startup form.</span></span>  
  
 <span data-ttu-id="04e3f-104">これは、場合に発生することができます、**アプリケーション フレームワークを有効にする**プロジェクト デザイナー チェック ボックスが選択されているが、**スタートアップ フォーム**が指定されていません。</span><span class="sxs-lookup"><span data-stu-id="04e3f-104">This can occur if the **Enable application framework** check box is selected in the project designer but the **Startup form** is not specified.</span></span> <span data-ttu-id="04e3f-105">詳細については、次を参照してください。[アプリケーション ページで、プロジェクト デザイナー) (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/application-page-project-designer-visual-basic)します。</span><span class="sxs-lookup"><span data-stu-id="04e3f-105">For more information, see [Application Page, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="04e3f-106">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="04e3f-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="04e3f-107">アプリケーションのスタートアップ オブジェクトを指定します。</span><span class="sxs-lookup"><span data-stu-id="04e3f-107">Specify a startup object for the application.</span></span>  
  
     <span data-ttu-id="04e3f-108">詳細については、次を参照してください。[アプリケーション ページで、プロジェクト デザイナー) (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/application-page-project-designer-visual-basic)します。</span><span class="sxs-lookup"><span data-stu-id="04e3f-108">For more information, see [Application Page, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span></span>  
  
2.  <span data-ttu-id="04e3f-109">オーバーライド、<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A>を設定するメソッド、<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A>プロパティをスタートアップ フォーム</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A></xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A>。</span><span class="sxs-lookup"><span data-stu-id="04e3f-109">Override the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A> method to set the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A> property to the startup form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04e3f-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="04e3f-110">See Also</span></span>  
 <span data-ttu-id="04e3f-111"><xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase></xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase></span><span class="sxs-lookup"><span data-stu-id="04e3f-111"><xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase></span></span>   
 <span data-ttu-id="04e3f-112"><xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A></xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A></span><span class="sxs-lookup"><span data-stu-id="04e3f-112"><xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A></span></span>   
 <span data-ttu-id="04e3f-113"><xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A></xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A></span><span class="sxs-lookup"><span data-stu-id="04e3f-113"><xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A></span></span>   
<span data-ttu-id="04e3f-114"> [Visual Basic アプリケーション モデルの概要](../../../visual-basic/developing-apps/development-with-my/overview-of-the-visual-basic-application-model.md)</span><span class="sxs-lookup"><span data-stu-id="04e3f-114"> [Overview of the Visual Basic Application Model](../../../visual-basic/developing-apps/development-with-my/overview-of-the-visual-basic-application-model.md)</span></span>

---
title: "ErrorProvider コンポーネントの概要 (Windows フォーム)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ErrorProvider
helpviewer_keywords:
- errors [Windows Forms], displaying to users
- error messages [Windows Forms], displaying
- ErrorProvider component [Windows Forms], about ErrorProvider component
ms.assetid: ced189f2-b5c8-46a7-a6f1-37f5af95dc99
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8b47e55461610d2cc4bf85c839ddb1bef937d69e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="errorprovider-component-overview-windows-forms"></a><span data-ttu-id="53965-102">ErrorProvider コンポーネントの概要 (Windows フォーム)</span><span class="sxs-lookup"><span data-stu-id="53965-102">ErrorProvider Component Overview (Windows Forms)</span></span>
<span data-ttu-id="53965-103">Windows フォーム[ErrorProvider](../../../../docs/framework/winforms/controls/errorprovider-component-windows-forms.md)コンポーネントは、フォームまたはコントロールのユーザー入力の検証に使用します。</span><span class="sxs-lookup"><span data-stu-id="53965-103">The Windows Forms [ErrorProvider](../../../../docs/framework/winforms/controls/errorprovider-component-windows-forms.md) component is used to validate user input on a form or control.</span></span> <span data-ttu-id="53965-104">通常、フォーム上のユーザー入力の検証またはデータセット内のエラーを表示すると組み合わせて使用されます。</span><span class="sxs-lookup"><span data-stu-id="53965-104">It is typically used in conjunction with validating user input on a form, or displaying errors within a dataset.</span></span> <span data-ttu-id="53965-105">エラー プロバイダーでは、エラー メッセージを表示するメッセージ ボックスより優れた選択肢をメッセージ ボックスが閉じられた後は、エラー メッセージが表示されないためです。</span><span class="sxs-lookup"><span data-stu-id="53965-105">An error provider is a better alternative than displaying an error message in a message box, because once a message box is dismissed, the error message is no longer visible.</span></span> <span data-ttu-id="53965-106"><xref:System.Windows.Forms.ErrorProvider>コンポーネントには、エラー アイコンが表示されます (![ErrorProvider アイコン](../../../../docs/framework/winforms/controls/media/vberrorprovidericon.gif "vbErrorProviderIcon"))、テキスト ボックスは、ユーザーが上にマウス ポインターを置いたときなど、関連するコントロールの横に、エラー アイコン、ツールヒントが表示されます、エラー メッセージ文字列を表示します。</span><span class="sxs-lookup"><span data-stu-id="53965-106">The <xref:System.Windows.Forms.ErrorProvider> component displays an error icon (![ErrorProvider icon](../../../../docs/framework/winforms/controls/media/vberrorprovidericon.gif "vbErrorProviderIcon")) next to the relevant control, such as a text box; when the user positions the mouse pointer over the error icon, a ToolTip appears, showing the error message string.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="53965-107">キー プロパティ</span><span class="sxs-lookup"><span data-stu-id="53965-107">Key Properties</span></span>  
 <span data-ttu-id="53965-108"><xref:System.Windows.Forms.ErrorProvider>コンポーネントのプロパティは<xref:System.Windows.Forms.ErrorProvider.DataSource%2A>、 <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A>、および<xref:System.Windows.Forms.ErrorProvider.Icon%2A>です。</span><span class="sxs-lookup"><span data-stu-id="53965-108">The <xref:System.Windows.Forms.ErrorProvider> component's key properties are <xref:System.Windows.Forms.ErrorProvider.DataSource%2A>, <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A>, and <xref:System.Windows.Forms.ErrorProvider.Icon%2A>.</span></span> <span data-ttu-id="53965-109">使用する場合<xref:System.Windows.Forms.ErrorProvider>コンポーネント、データ バインド コントロールを<xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A>プロパティは、エラー アイコンをフォームに表示する対象のコンポーネントの順序で適切なコンテナー (通常は Windows フォーム) に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="53965-109">When using <xref:System.Windows.Forms.ErrorProvider> component with data-bound controls, the <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A> property must be set to the appropriate container (usually the Windows Form) in order for the component to display an error icon on the form.</span></span> <span data-ttu-id="53965-110">デザイナーでコンポーネントを追加すると、<xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A>プロパティが対象のフォームに設定されている場合はコード内にコントロールを追加すると、設定することは必要があります自分でします。</span><span class="sxs-lookup"><span data-stu-id="53965-110">When the component is added in the designer, the <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A> property is set to the containing form; if you add the control in code, you must set it yourself.</span></span>  
  
 <span data-ttu-id="53965-111"><xref:System.Windows.Forms.ErrorProvider.Icon%2A>プロパティは、既定ではなく独自のエラー アイコンに設定することができます。</span><span class="sxs-lookup"><span data-stu-id="53965-111">The <xref:System.Windows.Forms.ErrorProvider.Icon%2A> property can be set to a custom error icon instead of the default.</span></span> <span data-ttu-id="53965-112">ときに、<xref:System.Windows.Forms.ErrorProvider.DataSource%2A>プロパティが設定されて、<xref:System.Windows.Forms.ErrorProvider>コンポーネントは、データセットのエラー メッセージを表示できます。</span><span class="sxs-lookup"><span data-stu-id="53965-112">When the <xref:System.Windows.Forms.ErrorProvider.DataSource%2A> property is set, the <xref:System.Windows.Forms.ErrorProvider> component can display error messages for a dataset.</span></span> <span data-ttu-id="53965-113">主要なメソッド、<xref:System.Windows.Forms.ErrorProvider>コンポーネントは、<xref:System.Windows.Forms.ErrorProvider.SetError%2A>メソッド、エラー メッセージ文字列を指定して、エラー アイコンが表示されます。</span><span class="sxs-lookup"><span data-stu-id="53965-113">The key method of the <xref:System.Windows.Forms.ErrorProvider> component is the <xref:System.Windows.Forms.ErrorProvider.SetError%2A> method, which specifies the error message string and where the error icon should appear.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="53965-114"><xref:System.Windows.Forms.ErrorProvider>コンポーネントがユーザー補助クライアントの組み込みサポートを提供していません。</span><span class="sxs-lookup"><span data-stu-id="53965-114">The <xref:System.Windows.Forms.ErrorProvider> component does not provide built-in support for accessibility clients.</span></span> <span data-ttu-id="53965-115">アプリケーション アクセスできるようにする場合、このコンポーネントを使用して、アクセス可能な追加のフィードバック メカニズムを提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="53965-115">To make your application accessible when using this component, you must provide an additional, accessible feedback mechanism.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53965-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="53965-116">See Also</span></span>  
 <xref:System.Windows.Forms.ErrorProvider>  
 [<span data-ttu-id="53965-117">方法: Windows フォーム ErrorProvider コンポーネントで DataSet 内にエラーを表示する</span><span class="sxs-lookup"><span data-stu-id="53965-117">How to: View Errors Within a DataSet with the Windows Forms ErrorProvider Component</span></span>](../../../../docs/framework/winforms/controls/view-errors-within-a-dataset-with-wf-errorprovider-component.md)  
 [<span data-ttu-id="53965-118">方法: Windows フォーム ErrorProvider コンポーネントを使用してフォーム検証でエラー アイコンを表示する</span><span class="sxs-lookup"><span data-stu-id="53965-118">How to: Display Error Icons for Form Validation with the Windows Forms ErrorProvider Component</span></span>](../../../../docs/framework/winforms/controls/display-error-icons-for-form-validation-with-wf-errorprovider.md)

---
title: Windows フォーム上のコントロールのユーザー補助情報の提供
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, accessibility
- controls [Windows Forms], accessibility
- accessibility [Windows Forms], Windows Forms controls
ms.assetid: 887dee6f-5059-4d57-957d-7c6fcd4acb10
ms.openlocfilehash: ffeecc1dfe52f1703fc201ef196644afbcc4708c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33536837"
---
# <a name="providing-accessibility-information-for-controls-on-a-windows-form"></a><span data-ttu-id="3f69e-102">Windows フォーム上のコントロールのユーザー補助情報の提供</span><span class="sxs-lookup"><span data-stu-id="3f69e-102">Providing Accessibility Information for Controls on a Windows Form</span></span>
<span data-ttu-id="3f69e-103">ユーザー補助機能は専用のプログラムおよびデバイスで、障碍を持つユーザーがコンピューターをより効果的に使用するよう助けます。</span><span class="sxs-lookup"><span data-stu-id="3f69e-103">Accessibility aids are specialized programs and devices that help people with disabilities use computers more effectively.</span></span> <span data-ttu-id="3f69e-104">たとえば、視覚障碍者のためのスクリーン リーダーや、マウスまたはキーボードではなく音声コマンド入力を利用するユーザーのための音声入力ユーティリティがあります。</span><span class="sxs-lookup"><span data-stu-id="3f69e-104">Examples include screen readers for people who are blind and voice input utilities for people who provide verbal commands instead of using the mouse or keyboard.</span></span> <span data-ttu-id="3f69e-105">これらのユーザー補助機能は、Windows フォーム コントロールによって公開されているアクセシビリティのプロパティと連携します。</span><span class="sxs-lookup"><span data-stu-id="3f69e-105">These accessibility aids interact with the accessibility properties exposed by Windows Forms controls.</span></span> <span data-ttu-id="3f69e-106">これらのプロパティとは:</span><span class="sxs-lookup"><span data-stu-id="3f69e-106">These properties are:</span></span>  
  
-   <span data-ttu-id="3f69e-107">**AccessibilityObject**</span><span class="sxs-lookup"><span data-stu-id="3f69e-107">**AccessibilityObject**</span></span>  
  
-   <span data-ttu-id="3f69e-108">**AccessibleDefaultActionDescription**</span><span class="sxs-lookup"><span data-stu-id="3f69e-108">**AccessibleDefaultActionDescription**</span></span>  
  
-   <span data-ttu-id="3f69e-109">**AccessibleDescription**</span><span class="sxs-lookup"><span data-stu-id="3f69e-109">**AccessibleDescription**</span></span>  
  
-   <span data-ttu-id="3f69e-110">**AccessibleName**</span><span class="sxs-lookup"><span data-stu-id="3f69e-110">**AccessibleName**</span></span>  
  
-   <span data-ttu-id="3f69e-111">**AccessibleRole**</span><span class="sxs-lookup"><span data-stu-id="3f69e-111">**AccessibleRole**</span></span>  
  
## <a name="accessibilityobject-property"></a><span data-ttu-id="3f69e-112">AccessibilityObject プロパティ</span><span class="sxs-lookup"><span data-stu-id="3f69e-112">AccessibilityObject Property</span></span>  
 <span data-ttu-id="3f69e-113">この読み取り専用プロパティには <xref:System.Windows.Forms.AccessibleObject> インスタンスが含まれます。</span><span class="sxs-lookup"><span data-stu-id="3f69e-113">This read-only property contains an <xref:System.Windows.Forms.AccessibleObject> instance.</span></span> <span data-ttu-id="3f69e-114">**AccessibleObject** は、コントロールの説明、画面上の位置、ナビゲーション能力、および値に関する情報を提供する <xref:Accessibility.IAccessible> インターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="3f69e-114">The **AccessibleObject** implements the <xref:Accessibility.IAccessible> interface, which provides information about the control's description, screen location, navigational abilities, and value.</span></span> <span data-ttu-id="3f69e-115">デザイナーは、コントロールがフォームに追加されたときにこの値を設定します。</span><span class="sxs-lookup"><span data-stu-id="3f69e-115">The designer sets this value when the control is added to the form.</span></span>  
  
## <a name="accessibledefaultactiondescription-property"></a><span data-ttu-id="3f69e-116">AccessibleDefaultActionDescription プロパティ</span><span class="sxs-lookup"><span data-stu-id="3f69e-116">AccessibleDefaultActionDescription Property</span></span>  
 <span data-ttu-id="3f69e-117">この文字列は、コントロールの操作について説明します。</span><span class="sxs-lookup"><span data-stu-id="3f69e-117">This string describes the action of the control.</span></span> <span data-ttu-id="3f69e-118">[プロパティ] ウィンドウには表示されず、コードでのみ設定できます。</span><span class="sxs-lookup"><span data-stu-id="3f69e-118">It does not appear in the Properties window and may only be set in code.</span></span> <span data-ttu-id="3f69e-119">次の例では、このプロパティをボタン コントロールに設定します。</span><span class="sxs-lookup"><span data-stu-id="3f69e-119">The following example sets this property for a button control:</span></span>  
  
```  
' Visual Basic  
Button1.AccessibleDefaultActionDescription = _  
   "Closes the application."  
  
// C#  
Button1.AccessibleDefaultActionDescription =   
   "Closes the application.";  
  
// C++  
button1->AccessibleDefaultActionDescription =  
   "Closes the application.";  
```  
  
## <a name="accessibledescription-property"></a><span data-ttu-id="3f69e-120">AccessibleDescription プロパティ</span><span class="sxs-lookup"><span data-stu-id="3f69e-120">AccessibleDescription Property</span></span>  
 <span data-ttu-id="3f69e-121">この文字列はコントロールについて説明します。</span><span class="sxs-lookup"><span data-stu-id="3f69e-121">This string describes the control.</span></span> <span data-ttu-id="3f69e-122">これは、[プロパティ] ウィンドウで、または次のようにコードで設定できます。</span><span class="sxs-lookup"><span data-stu-id="3f69e-122">It may be set in the Properties window, or in code as follows:</span></span>  
  
```  
' Visual Basic  
Button1.AccessibleDescription = "A button with text 'Exit'."  
  
// C#  
Button1.AccessibleDescription = "A button with text 'Exit'";  
  
// C++  
button1->AccessibleDescription = "A button with text 'Exit'";  
```  
  
## <a name="accessiblename-property"></a><span data-ttu-id="3f69e-123">AccessibleName プロパティ</span><span class="sxs-lookup"><span data-stu-id="3f69e-123">AccessibleName Property</span></span>  
 <span data-ttu-id="3f69e-124">これは、ユーザー補助機能に報告されたコントロールの名前です。</span><span class="sxs-lookup"><span data-stu-id="3f69e-124">This is the name of a control reported to accessibility aids.</span></span> <span data-ttu-id="3f69e-125">これは、[プロパティ] ウィンドウで、または次のようにコードで設定できます。</span><span class="sxs-lookup"><span data-stu-id="3f69e-125">It may be set in the Properties window, or in code as follows:</span></span>  
  
```  
' Visual Basic  
Button1.AccessibleName = "Order"  
  
// C#  
Button1.AccessibleName = "Order";  
  
// C++  
button1->AccessibleName = "Order";  
```  
  
## <a name="accessiblerole-property"></a><span data-ttu-id="3f69e-126">AccessibleRole プロパティ</span><span class="sxs-lookup"><span data-stu-id="3f69e-126">AccessibleRole Property</span></span>  
 <span data-ttu-id="3f69e-127">このプロパティには <xref:System.Windows.Forms.AccessibleRole> 列挙型が含まれており、コントロールのユーザー インターフェイスの役割について説明します。</span><span class="sxs-lookup"><span data-stu-id="3f69e-127">This property, which contains an <xref:System.Windows.Forms.AccessibleRole> enumeration, describes the user interface role of the control.</span></span> <span data-ttu-id="3f69e-128">新しいコントロールは値が `Default`に設定されています。</span><span class="sxs-lookup"><span data-stu-id="3f69e-128">A new control has the value set to `Default`.</span></span> <span data-ttu-id="3f69e-129">つまり、 **ボタン** コントロールは既定値では **ボタン**として機能します。</span><span class="sxs-lookup"><span data-stu-id="3f69e-129">This would mean that by default, a **Button** control acts as a **Button**.</span></span> <span data-ttu-id="3f69e-130">コントロールに別の役割がある場合、このプロパティをリセットできます。</span><span class="sxs-lookup"><span data-stu-id="3f69e-130">You may want to reset this property if a control has another role.</span></span> <span data-ttu-id="3f69e-131">たとえば、 **PictureBox** コントロールを **Chart**として使用する場合、 **PictureBox**ではなく **Chart**としてユーザー補助機能が役割を報告するようにできます。</span><span class="sxs-lookup"><span data-stu-id="3f69e-131">For example, you may be using a **PictureBox** control as a **Chart**, and you may want accessibility aids to report the role as a **Chart**, not as a **PictureBox**.</span></span> <span data-ttu-id="3f69e-132">また、開発したカスタム コントロールにこのプロパティを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="3f69e-132">You may also want to specify this property for custom controls you have developed.</span></span> <span data-ttu-id="3f69e-133">このプロパティは、[プロパティ] ウィンドウで、または次のようにコードで設定できます。</span><span class="sxs-lookup"><span data-stu-id="3f69e-133">This property may be set in the Properties window, or in code as follows:</span></span>  
  
```  
' Visual Basic  
PictureBox1.AccessibleRole = AccessibleRole.Chart  
  
// C#  
PictureBox1.AccessibleRole = AccessibleRole.Chart;  
  
// C++  
pictureBox1->AccessibleRole = AccessibleRole::Chart;  
```  
  
## <a name="see-also"></a><span data-ttu-id="3f69e-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="3f69e-134">See Also</span></span>  
 <xref:System.Windows.Forms.AccessibleObject>  
 <xref:System.Windows.Forms.Control.AccessibilityObject%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Control.AccessibleDefaultActionDescription%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Control.AccessibleDescription%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Control.AccessibleName%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Control.AccessibleRole%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.AccessibleRole>

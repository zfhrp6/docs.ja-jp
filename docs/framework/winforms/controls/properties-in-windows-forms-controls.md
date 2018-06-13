---
title: Windows フォーム コントロールのプロパティ
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], properties overview (using code)
- controls [Windows Forms], properties
- properties [Windows Forms]
ms.assetid: 2785279b-fb57-4937-8f6b-2050e475db6f
ms.openlocfilehash: aa7d8be158f4e0a7b2b95bf02cb0d1e173041f59
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33538130"
---
# <a name="properties-in-windows-forms-controls"></a><span data-ttu-id="37e22-102">Windows フォーム コントロールのプロパティ</span><span class="sxs-lookup"><span data-stu-id="37e22-102">Properties in Windows Forms Controls</span></span>
<span data-ttu-id="37e22-103">Windows フォーム コントロールは多くのプロパティ フォームの基本クラスを継承して<xref:System.Windows.Forms.Control?displayProperty=nameWithType>です。</span><span class="sxs-lookup"><span data-stu-id="37e22-103">A Windows Forms control inherits many properties form the base class <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span></span> <span data-ttu-id="37e22-104">などのプロパティが含まれます<xref:System.Windows.Forms.Control.Font%2A>、 <xref:System.Windows.Forms.Control.ForeColor%2A>、 <xref:System.Windows.Forms.Control.BackColor%2A>、 <xref:System.Windows.Forms.Control.Bounds%2A>、 <xref:System.Windows.Forms.Control.ClientRectangle%2A>、 <xref:System.Windows.Forms.Control.DisplayRectangle%2A>、 <xref:System.Windows.Forms.Control.Enabled%2A>、 <xref:System.Windows.Forms.Control.Focused%2A>、 <xref:System.Windows.Forms.Control.Height%2A>、 <xref:System.Windows.Forms.Control.Width%2A>、 <xref:System.Windows.Forms.Control.Visible%2A>、 <xref:System.Windows.Forms.Control.AutoSize%2A>、およびその他の多くのです。</span><span class="sxs-lookup"><span data-stu-id="37e22-104">These include properties such as <xref:System.Windows.Forms.Control.Font%2A>, <xref:System.Windows.Forms.Control.ForeColor%2A>, <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.Bounds%2A>, <xref:System.Windows.Forms.Control.ClientRectangle%2A>, <xref:System.Windows.Forms.Control.DisplayRectangle%2A>, <xref:System.Windows.Forms.Control.Enabled%2A>, <xref:System.Windows.Forms.Control.Focused%2A>, <xref:System.Windows.Forms.Control.Height%2A>, <xref:System.Windows.Forms.Control.Width%2A>, <xref:System.Windows.Forms.Control.Visible%2A>, <xref:System.Windows.Forms.Control.AutoSize%2A>, and many others.</span></span> <span data-ttu-id="37e22-105">詳細については、継承されたプロパティは、次を参照してください。<xref:System.Windows.Forms.Control?displayProperty=nameWithType>です。</span><span class="sxs-lookup"><span data-stu-id="37e22-105">For details about inherited properties, see <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="37e22-106">コントロールで継承されたプロパティをオーバーライドしたり、新しいプロパティを定義したりできます。</span><span class="sxs-lookup"><span data-stu-id="37e22-106">You can override inherited properties in your control as well as define new properties.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="37e22-107">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="37e22-107">In This Section</span></span>  
 [<span data-ttu-id="37e22-108">プロパティの定義</span><span class="sxs-lookup"><span data-stu-id="37e22-108">Defining a Property</span></span>](../../../../docs/framework/winforms/controls/defining-a-property-in-windows-forms-controls.md)  
 <span data-ttu-id="37e22-109">カスタム コントロールまたはカスタム コンポーネントのプロパティを実装する方法と、そのプロパティをデザイン環境に統合する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="37e22-109">Shows how to implement a property for a custom control or component and shows how to integrate the property into the design environment.</span></span>  
  
 [<span data-ttu-id="37e22-110">ShouldSerialize メソッドと Reset メソッドによる既定値の定義</span><span class="sxs-lookup"><span data-stu-id="37e22-110">Defining Default Values with the ShouldSerialize and Reset Methods</span></span>](../../../../docs/framework/winforms/controls/defining-default-values-with-the-shouldserialize-and-reset-methods.md)  
 <span data-ttu-id="37e22-111">カスタム コントロールまたはカスタム コンポーネントの既定のプロパティ値を定義する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="37e22-111">Shows how to define default property values for a custom control or component.</span></span>  
  
 [<span data-ttu-id="37e22-112">プロパティ変更イベント</span><span class="sxs-lookup"><span data-stu-id="37e22-112">Property-Changed Events</span></span>](../../../../docs/framework/winforms/controls/property-changed-events.md)  
 <span data-ttu-id="37e22-113">プロパティ値が変更されたときに、プロパティ変更通知を有効にする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="37e22-113">Describes how to enable property-change notifications when a property value changes.</span></span>  
  
 [<span data-ttu-id="37e22-114">方法 : 内在コントロールのプロパティを公開する</span><span class="sxs-lookup"><span data-stu-id="37e22-114">How to: Expose Properties of Constituent Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-expose-properties-of-constituent-controls.md)  
 <span data-ttu-id="37e22-115">カスタム複合コントロール内の内在コントロールのプロパティを公開する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="37e22-115">Shows how to expose properties of constituent controls in a custom composite control.</span></span>  
  
 [<span data-ttu-id="37e22-116">カスタム コントロールへのメソッドの実装</span><span class="sxs-lookup"><span data-stu-id="37e22-116">Method Implementation in Custom Controls</span></span>](../../../../docs/framework/winforms/controls/method-implementation-in-custom-controls.md)  
 <span data-ttu-id="37e22-117">カスタム コントロールおよびカスタム コンポーネントにメソッドを実装する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="37e22-117">Describes how to implement methods in custom controls and components.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="37e22-118">参照</span><span class="sxs-lookup"><span data-stu-id="37e22-118">Reference</span></span>  
 <xref:System.Windows.Forms.UserControl>  
 <span data-ttu-id="37e22-119">複合コントロールを実装するための基本クラスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="37e22-119">Documents the base class for implementing composite controls.</span></span>  
  
 <xref:System.ComponentModel.TypeConverterAttribute>  
 <span data-ttu-id="37e22-120">指定する属性をドキュメント、<xref:System.ComponentModel.TypeConverter>カスタム プロパティの型を使用します。</span><span class="sxs-lookup"><span data-stu-id="37e22-120">Documents the attribute that specifies the <xref:System.ComponentModel.TypeConverter> to use for a custom property type.</span></span>  
  
 <xref:System.ComponentModel.EditorAttribute>  
 <span data-ttu-id="37e22-121">指定する属性をドキュメント、<xref:System.Drawing.Design.UITypeEditor>カスタム プロパティに使用します。</span><span class="sxs-lookup"><span data-stu-id="37e22-121">Documents the attribute that specifies the <xref:System.Drawing.Design.UITypeEditor> to use for a custom property.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="37e22-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="37e22-122">Related Sections</span></span>  
 [<span data-ttu-id="37e22-123">Windows フォーム コントロールの属性</span><span class="sxs-lookup"><span data-stu-id="37e22-123">Attributes in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/attributes-in-windows-forms-controls.md)  
 <span data-ttu-id="37e22-124">カスタム コントロールとコンポーネントのプロパティや他のメンバーに適用できる属性について説明します。</span><span class="sxs-lookup"><span data-stu-id="37e22-124">Describes the attributes you can apply to properties or other members of your custom controls and components.</span></span>  
  
 [<span data-ttu-id="37e22-125">コンポーネントのデザイン時属性</span><span class="sxs-lookup"><span data-stu-id="37e22-125">Design-Time Attributes for Components</span></span>](http://msdn.microsoft.com/library/12050fe3-9327-4509-9e21-4ee2494b95c3)  
 <span data-ttu-id="37e22-126">ビジュアル デザイナーでデザインするときに正しく表示されるようにコンポーネントとコントロールに適用するメタデータ属性の一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="37e22-126">Lists metadata attributes to apply to components and controls so that they are displayed correctly at design time in visual designers.</span></span>  
  
 [<span data-ttu-id="37e22-127">デザイン時サポートの拡張</span><span class="sxs-lookup"><span data-stu-id="37e22-127">Extending Design-Time Support</span></span>](http://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)  
 <span data-ttu-id="37e22-128">デザイン時サポートを提供するエディターやデザイナーなどのクラスを実装する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="37e22-128">Describes how to implement classes such as editors and designers that provide design-time support.</span></span>

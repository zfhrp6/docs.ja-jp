---
title: Windows フォーム コントロールの属性
ms.date: 03/30/2017
helpviewer_keywords:
- attributes [Windows Forms]
- attributes [Windows Forms], data binding properties
- attributes [Windows Forms], control properties
- attributes [Windows Forms], classes
ms.assetid: 2c5640e9-6c6c-49d7-a5e4-a768f6be7853
ms.openlocfilehash: e06836e53a69394ad899bedc8e545dbff9b9c29d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33525779"
---
# <a name="attributes-in-windows-forms-controls"></a><span data-ttu-id="23464-102">Windows フォーム コントロールの属性</span><span class="sxs-lookup"><span data-stu-id="23464-102">Attributes in Windows Forms Controls</span></span>
<span data-ttu-id="23464-103">.NET Framework には、カスタム コントロールおよびカスタム コンポーネントのメンバーに適用できるさまざまな属性が用意されています。</span><span class="sxs-lookup"><span data-stu-id="23464-103">The .NET Framework provides a variety of attributes you can apply to the members of your custom controls and components.</span></span> <span data-ttu-id="23464-104">これらの属性には、クラスの実行時の動作に影響を及ぼすものもあれば、デザイン時の動作に影響を及ぼすものもあります。</span><span class="sxs-lookup"><span data-stu-id="23464-104">Some of these attributes affect the run-time behavior of a class, and others affect the design-time behavior.</span></span>  
  
## <a name="attributes-for-control-and-component-properties"></a><span data-ttu-id="23464-105">コントロールおよびコンポーネントのプロパティの属性</span><span class="sxs-lookup"><span data-stu-id="23464-105">Attributes for Control and Component Properties</span></span>  
 <span data-ttu-id="23464-106">次の表には、カスタム コントロールおよびカスタム コンポーネントのプロパティや他のメンバーに適用できる属性が示されています。</span><span class="sxs-lookup"><span data-stu-id="23464-106">The following table shows the attributes you can apply to properties or other members of your custom controls and components.</span></span> <span data-ttu-id="23464-107">これらの属性の多くの使用例については、「[方法: Windows フォーム コントロールに属性を適用する](../../../../docs/framework/winforms/controls/how-to-apply-attributes-in-windows-forms-controls.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="23464-107">For an example that uses many of these attributes, see [How to: Apply Attributes in Windows Forms Controls](../../../../docs/framework/winforms/controls/how-to-apply-attributes-in-windows-forms-controls.md).</span></span>  
  
|<span data-ttu-id="23464-108">属性</span><span class="sxs-lookup"><span data-stu-id="23464-108">Attribute</span></span>|<span data-ttu-id="23464-109">説明</span><span class="sxs-lookup"><span data-stu-id="23464-109">Description</span></span>|  
|---------------|-----------------|  
|<xref:System.ComponentModel.AmbientValueAttribute>|<span data-ttu-id="23464-110">プロパティに渡す値を指定し、そのプロパティが別のソースから値を取得するようにします。</span><span class="sxs-lookup"><span data-stu-id="23464-110">Specifies the value to pass to a property to cause the property to get its value from another source.</span></span> <span data-ttu-id="23464-111">これは "*アンビエンス*" と呼ばれています。</span><span class="sxs-lookup"><span data-stu-id="23464-111">This is known as *ambience*.</span></span>|  
|<xref:System.ComponentModel.BrowsableAttribute>|<span data-ttu-id="23464-112">プロパティまたはイベントが **[プロパティ]** ウィンドウに表示されるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="23464-112">Specifies whether a property or event should be displayed in a **Properties** window.</span></span>|  
|<xref:System.ComponentModel.CategoryAttribute>|<span data-ttu-id="23464-113">プロパティまたはイベントに表示される場合にグループ化するためのカテゴリの名前を指定します、<xref:System.Windows.Forms.PropertyGrid>コントロールに対して設定<xref:System.Windows.Forms.PropertySort.Categorized>モード。</span><span class="sxs-lookup"><span data-stu-id="23464-113">Specifies the name of the category in which to group the property or event when displayed in a <xref:System.Windows.Forms.PropertyGrid> control set to <xref:System.Windows.Forms.PropertySort.Categorized> mode.</span></span>|  
|<xref:System.ComponentModel.DefaultValueAttribute>|<span data-ttu-id="23464-114">プロパティの既定値を指定します。</span><span class="sxs-lookup"><span data-stu-id="23464-114">Specifies the default value for a property.</span></span>|  
|<xref:System.ComponentModel.DescriptionAttribute>|<span data-ttu-id="23464-115">プロパティまたはイベントの説明文を指定します。</span><span class="sxs-lookup"><span data-stu-id="23464-115">Specifies a description for a property or event.</span></span>|  
|<xref:System.ComponentModel.DisplayNameAttribute>|<span data-ttu-id="23464-116">引数を受け取らないプロパティ、イベント、または `public``void` メソッドの表示名を指定します。</span><span class="sxs-lookup"><span data-stu-id="23464-116">Specifies the display name for a property, event, or `public``void` method that takes no arguments.</span></span>|  
|<xref:System.ComponentModel.EditorAttribute>|<span data-ttu-id="23464-117">プロパティの変更に使用するエディターを指定します。</span><span class="sxs-lookup"><span data-stu-id="23464-117">Specifies the editor to use to change a property.</span></span>|  
|<xref:System.ComponentModel.EditorBrowsableAttribute>|<span data-ttu-id="23464-118">プロパティまたはメソッドをエディターで表示できるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="23464-118">Specifies that a property or method is viewable in an editor.</span></span>|  
|<xref:System.ComponentModel.Design.HelpKeywordAttribute>|<span data-ttu-id="23464-119">クラスまたはメンバーのコンテキスト キーワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="23464-119">Specifies the context keyword for a class or member.</span></span>|  
|<xref:System.ComponentModel.LocalizableAttribute>|<span data-ttu-id="23464-120">プロパティをローカライズする必要があるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="23464-120">Specifies whether a property should be localized.</span></span>|  
|<xref:System.ComponentModel.PasswordPropertyTextAttribute>|<span data-ttu-id="23464-121">アスタリスクなどの文字で、オブジェクトのテキスト表記を隠すように指示します。</span><span class="sxs-lookup"><span data-stu-id="23464-121">Indicates that an object's text representation is obscured by characters such as asterisks.</span></span>|  
|<xref:System.ComponentModel.ReadOnlyAttribute>|<span data-ttu-id="23464-122">デザイン時に、この属性がバインドされるプロパティが読み取り専用か読み取り/書き込み可能かを指定します。</span><span class="sxs-lookup"><span data-stu-id="23464-122">Specifies whether the property this attribute is bound to is read-only or read/write at design time.</span></span>|  
|<xref:System.ComponentModel.RefreshPropertiesAttribute>|<span data-ttu-id="23464-123">関連付けられているプロパティ値が変更されたときに、プロパティ グリッドが更新されるように指定します。</span><span class="sxs-lookup"><span data-stu-id="23464-123">Indicates that the property grid should refresh when the associated property value changes.</span></span>|  
|<xref:System.ComponentModel.TypeConverterAttribute>|<span data-ttu-id="23464-124">この属性が関連付けられているオブジェクトのコンバーターとして使用する型を指定します。</span><span class="sxs-lookup"><span data-stu-id="23464-124">Specifies what type to use as a converter for the object this attribute is bound to.</span></span>|  
  
## <a name="attributes-for-data-binding-properties"></a><span data-ttu-id="23464-125">データ バインディング プロパティの属性</span><span class="sxs-lookup"><span data-stu-id="23464-125">Attributes for Data Binding Properties</span></span>  
 <span data-ttu-id="23464-126">次の表には、カスタム コントロールおよびカスタム コンポーネントがデータ バインディングと相互作用する方法を指定するために適用できる属性が示されています。</span><span class="sxs-lookup"><span data-stu-id="23464-126">The following table shows the attributes you can apply to specify how your custom controls and components interact with data binding.</span></span>  
  
|<span data-ttu-id="23464-127">属性</span><span class="sxs-lookup"><span data-stu-id="23464-127">Attribute</span></span>|<span data-ttu-id="23464-128">説明</span><span class="sxs-lookup"><span data-stu-id="23464-128">Description</span></span>|  
|---------------|-----------------|  
|<xref:System.ComponentModel.BindableAttribute>|<span data-ttu-id="23464-129">バインディングにプロパティが通常、使用されるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="23464-129">Specifies whether a property is typically used for binding.</span></span>|  
|<xref:System.ComponentModel.ComplexBindingPropertiesAttribute>|<span data-ttu-id="23464-130">コンポーネントのデータ ソースおよびデータ メンバーのプロパティを指定します。</span><span class="sxs-lookup"><span data-stu-id="23464-130">Specifies the data source and data member properties for a component.</span></span>|  
|<xref:System.ComponentModel.DefaultBindingPropertyAttribute>|<span data-ttu-id="23464-131">コンポーネントの既定のバインディング プロパティを指定します。</span><span class="sxs-lookup"><span data-stu-id="23464-131">Specifies the default binding property for a component.</span></span>|  
|<xref:System.ComponentModel.LookupBindingPropertiesAttribute>|<span data-ttu-id="23464-132">コンポーネントのデータ ソースおよびデータ メンバーのプロパティを指定します。</span><span class="sxs-lookup"><span data-stu-id="23464-132">Specifies the data source and data member properties for a component.</span></span>|  
|<xref:System.ComponentModel.AttributeProviderAttribute>|<span data-ttu-id="23464-133">属性のリダイレクトを有効にします。</span><span class="sxs-lookup"><span data-stu-id="23464-133">Enables attribute redirection.</span></span>|  
  
## <a name="attributes-for-classes"></a><span data-ttu-id="23464-134">クラスの属性</span><span class="sxs-lookup"><span data-stu-id="23464-134">Attributes for Classes</span></span>  
 <span data-ttu-id="23464-135">次の表には、デザイン時にカスタム コントロールおよびカスタム コンポーネントの動作を指定するために適用できる属性が示されています。</span><span class="sxs-lookup"><span data-stu-id="23464-135">The following table shows the attributes you can apply to specify the behavior of your custom controls and components at design time.</span></span>  
  
|<span data-ttu-id="23464-136">属性</span><span class="sxs-lookup"><span data-stu-id="23464-136">Attribute</span></span>|<span data-ttu-id="23464-137">説明</span><span class="sxs-lookup"><span data-stu-id="23464-137">Description</span></span>|  
|---------------|-----------------|  
|<xref:System.ComponentModel.DefaultEventAttribute>|<span data-ttu-id="23464-138">コンポーネントの既定のイベントを指定します。</span><span class="sxs-lookup"><span data-stu-id="23464-138">Specifies the default event for a component.</span></span>|  
|<xref:System.ComponentModel.DefaultPropertyAttribute>|<span data-ttu-id="23464-139">コンポーネントの既定のプロパティを指定します。</span><span class="sxs-lookup"><span data-stu-id="23464-139">Specifies the default property for a component.</span></span>|  
|<xref:System.ComponentModel.DesignerAttribute>|<span data-ttu-id="23464-140">コンポーネントのデザイン時サービスを実装するために使用されるクラスを指定します。</span><span class="sxs-lookup"><span data-stu-id="23464-140">Specifies the class used to implement design-time services for a component.</span></span>|  
|<xref:System.ComponentModel.DesignerCategoryAttribute>|<span data-ttu-id="23464-141">クラスのデザイナーが特定のカテゴリに属することを指定します。</span><span class="sxs-lookup"><span data-stu-id="23464-141">Specifies that the designer for a class belongs to a certain category.</span></span>|  
|<xref:System.ComponentModel.ToolboxItemAttribute>|<span data-ttu-id="23464-142">ツールボックス項目の属性を表します。</span><span class="sxs-lookup"><span data-stu-id="23464-142">Represents an attribute of a toolbox item.</span></span>|  
|<xref:System.ComponentModel.ToolboxItemFilterAttribute>|<span data-ttu-id="23464-143">ツールボックス項目に使用するフィルター文字列とフィルターの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="23464-143">Specifies the filter string and filter type to use for a Toolbox item.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="23464-144">関連項目</span><span class="sxs-lookup"><span data-stu-id="23464-144">See Also</span></span>  
 <xref:System.Attribute>  
 [<span data-ttu-id="23464-145">方法: Windows フォーム コントロールに属性を適用する</span><span class="sxs-lookup"><span data-stu-id="23464-145">How to: Apply Attributes in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-apply-attributes-in-windows-forms-controls.md)  
 [<span data-ttu-id="23464-146">デザイン時サポートの拡張</span><span class="sxs-lookup"><span data-stu-id="23464-146">Extending Design-Time Support</span></span>](http://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)  
 [<span data-ttu-id="23464-147">.NET Framework を使用したカスタム Windows フォーム コントロールの開発</span><span class="sxs-lookup"><span data-stu-id="23464-147">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)

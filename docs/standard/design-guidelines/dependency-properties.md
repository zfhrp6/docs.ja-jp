---
title: 依存関係プロパティ
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 212cfb1e-cec4-4047-94a6-47209b387f6f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 039015f895a491d8709815d6aff52eb6139d779f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33576117"
---
# <a name="dependency-properties"></a><span data-ttu-id="9a989-102">依存関係プロパティ</span><span class="sxs-lookup"><span data-stu-id="9a989-102">Dependency Properties</span></span>
<span data-ttu-id="9a989-103">依存関係プロパティ (DP) は、たとえば (フィールド) の型の変数に保存することではなく、プロパティ ストア内の値を格納する標準プロパティです。</span><span class="sxs-lookup"><span data-stu-id="9a989-103">A dependency property (DP) is a regular property that stores its value in a property store instead of storing it in a type variable (field), for example.</span></span>  
  
 <span data-ttu-id="9a989-104">割り当てられた依存プロパティはオブジェクトとそのコンテナーの間のリレーションシップを記述する「プロパティ」を表す、Get および Set の静的メソッドとしてモデル化された依存関係プロパティの種類 (の位置など、`Button`上のオブジェクト、 `Panel`コンテナー) です。</span><span class="sxs-lookup"><span data-stu-id="9a989-104">An attached dependency property is a kind of dependency property modeled as static Get and Set methods representing "properties" describing relationships between objects and their containers (e.g., the position of a `Button` object on a `Panel` container).</span></span>  
  
 <span data-ttu-id="9a989-105">**✓ しないで**プロパティ スタイル設定、トリガー、データ バインディング、アニメーション、動的なリソース、および継承などの WPF 機能をサポートする必要がある場合は、依存関係プロパティを提供します。</span><span class="sxs-lookup"><span data-stu-id="9a989-105">**✓ DO** provide the dependency properties, if you need the properties to support WPF features such as styling, triggers, data binding, animations, dynamic resources, and inheritance.</span></span>  
  
## <a name="dependency-property-design"></a><span data-ttu-id="9a989-106">依存関係プロパティのデザイン</span><span class="sxs-lookup"><span data-stu-id="9a989-106">Dependency Property Design</span></span>  
 <span data-ttu-id="9a989-107">**✓ しないで**から継承<xref:System.Windows.DependencyObject>、または依存関係プロパティを実装する場合、そのサブタイプのいずれか。</span><span class="sxs-lookup"><span data-stu-id="9a989-107">**✓ DO** inherit from <xref:System.Windows.DependencyObject>, or one of its subtypes, when implementing dependency properties.</span></span> <span data-ttu-id="9a989-108">種類は、プロパティ ストアの非常に効率的な実装を提供し、自動的に WPF データ バインディングをサポートします。</span><span class="sxs-lookup"><span data-stu-id="9a989-108">The type provides a very efficient implementation of a property store and automatically supports WPF data binding.</span></span>  
  
 <span data-ttu-id="9a989-109">**✓ しないで**正規の CLR プロパティとパブリックな静的読み取り専用フィールドのインスタンスを格納する提供<xref:System.Windows.DependencyProperty?displayProperty=nameWithType>各依存関係プロパティです。</span><span class="sxs-lookup"><span data-stu-id="9a989-109">**✓ DO** provide a regular CLR property and public static read-only field storing an instance of <xref:System.Windows.DependencyProperty?displayProperty=nameWithType> for each dependency property.</span></span>  
  
 <span data-ttu-id="9a989-110">**✓ しないで**依存関係プロパティを実装するインスタンス メソッドを呼び出すことによって<xref:System.Windows.DependencyObject.GetValue%2A?displayProperty=nameWithType>と<xref:System.Windows.DependencyObject.SetValue%2A?displayProperty=nameWithType>です。</span><span class="sxs-lookup"><span data-stu-id="9a989-110">**✓ DO** implement dependency properties by calling instance methods <xref:System.Windows.DependencyObject.GetValue%2A?displayProperty=nameWithType> and <xref:System.Windows.DependencyObject.SetValue%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="9a989-111">**✓ しないで**"Property"のプロパティの名前をアスタリスクの依存関係プロパティの静的フィールドの名前</span><span class="sxs-lookup"><span data-stu-id="9a989-111">**✓ DO** name the dependency property static field by suffixing the name of the property with "Property."</span></span>  
  
 <span data-ttu-id="9a989-112">**X しないで**コード内の依存関係プロパティの既定値を明示的に設定を代わりにメタデータの設定です。</span><span class="sxs-lookup"><span data-stu-id="9a989-112">**X DO NOT** set default values of dependency properties explicitly in code; set them in metadata instead.</span></span>  
  
 <span data-ttu-id="9a989-113">プロパティの既定値を明示的に設定するから、スタイルなどのいくつかの暗黙的な方法で設定されているそのプロパティをできない場合があります。</span><span class="sxs-lookup"><span data-stu-id="9a989-113">If you set a property default explicitly, you might prevent that property from being set by some implicit means, such as a styling.</span></span>  
  
 <span data-ttu-id="9a989-114">**X しないで**静的フィールドにアクセスする標準コード以外のプロパティ アクセサーにコードを配置します。</span><span class="sxs-lookup"><span data-stu-id="9a989-114">**X DO NOT** put code in the property accessors other than the standard code to access the static field.</span></span>  
  
 <span data-ttu-id="9a989-115">静的フィールドを直接使用するコードはありませんは実行、スタイルなどの暗黙的な方法で、プロパティが設定されている場合のスタイルを設定するためです。</span><span class="sxs-lookup"><span data-stu-id="9a989-115">That code won’t execute if the property is set by implicit means, such as a styling, because styling uses the static field directly.</span></span>  
  
 <span data-ttu-id="9a989-116">**X しないで**依存関係プロパティを使用してセキュリティで保護されたデータを格納します。</span><span class="sxs-lookup"><span data-stu-id="9a989-116">**X DO NOT** use dependency properties to store secure data.</span></span> <span data-ttu-id="9a989-117">さらにプライベート依存関係プロパティをパブリックにアクセスすることができます。</span><span class="sxs-lookup"><span data-stu-id="9a989-117">Even private dependency properties can be accessed publicly.</span></span>  
  
## <a name="attached-dependency-property-design"></a><span data-ttu-id="9a989-118">接続されている依存関係プロパティのデザイン</span><span class="sxs-lookup"><span data-stu-id="9a989-118">Attached Dependency Property Design</span></span>  
 <span data-ttu-id="9a989-119">前のセクションで説明されている依存関係プロパティの宣言する型の組み込みのプロパティを表しますたとえば、`Text`プロパティは、プロパティの`TextButton`を宣言しています。</span><span class="sxs-lookup"><span data-stu-id="9a989-119">Dependency properties described in the preceding section represent intrinsic properties of the declaring type; for example, the `Text` property is a property of `TextButton`, which declares it.</span></span> <span data-ttu-id="9a989-120">依存関係プロパティの特別な種類は、接続されている依存関係プロパティです。</span><span class="sxs-lookup"><span data-stu-id="9a989-120">A special kind of dependency property is the attached dependency property.</span></span>  
  
 <span data-ttu-id="9a989-121">添付プロパティの典型的な例は、<xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="9a989-121">A classic example of an attached property is the <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="9a989-122">プロパティ ボタン (いないグリッドの) 列の位置を表すは"にアタッチされて"ボタン グリッドで、グリッドで、ボタンが含まれている場合にのみ関連します。</span><span class="sxs-lookup"><span data-stu-id="9a989-122">The property represents Button’s (not Grid’s) column position, but it is only relevant if the Button is contained in a Grid, and so it's "attached" to Buttons by Grids.</span></span>  
  
```  
<Grid>  
    <Grid.ColumnDefinitions>  
        <ColumnDefinition />  
        <ColumnDefinition />  
    </Grid.ColumnDefinitions>  
  
    <Button Grid.Column="0">Click</Button>  
    <Button Grid.Column="1">Clack</Button>  
</Grid>  
```  
  
 <span data-ttu-id="9a989-123">添付プロパティの定義は、アクセサーが静的の Get および Set メソッドによって表される点を除いて、ほとんどの場合と同様に、通常の依存関係プロパティの検索します。</span><span class="sxs-lookup"><span data-stu-id="9a989-123">The definition of an attached property looks mostly like that of a regular dependency property, except that the accessors are represented by static Get and Set methods:</span></span>  
  
```  
public class Grid {  
  
    public static int GetColumn(DependencyObject obj) {  
        return (int)obj.GetValue(ColumnProperty);  
    }  
  
    public static void SetColumn(DependencyObject obj, int value) {  
        obj.SetValue(ColumnProperty,value);  
    }  
  
    public static readonly DependencyProperty ColumnProperty =  
        DependencyProperty.RegisterAttached(  
            "Column",  
            typeof(int),  
            typeof(Grid)  
    );  
}  
```  
  
## <a name="dependency-property-validation"></a><span data-ttu-id="9a989-124">依存関係プロパティの検証</span><span class="sxs-lookup"><span data-stu-id="9a989-124">Dependency Property Validation</span></span>  
 <span data-ttu-id="9a989-125">プロパティは、多くの場合、検証と呼ばれるものを実装します。</span><span class="sxs-lookup"><span data-stu-id="9a989-125">Properties often implement what is called validation.</span></span> <span data-ttu-id="9a989-126">プロパティの値を変更する試みが行われたときに検証ロジックを実行します。</span><span class="sxs-lookup"><span data-stu-id="9a989-126">Validation logic executes when an attempt is made to change the value of a property.</span></span>  
  
 <span data-ttu-id="9a989-127">残念なことに依存関係プロパティのアクセサーでは、任意の検証コードを含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="9a989-127">Unfortunately dependency property accessors cannot contain arbitrary validation code.</span></span> <span data-ttu-id="9a989-128">代わりに、依存関係プロパティの検証ロジックは、プロパティの登録中に指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9a989-128">Instead, dependency property validation logic needs to be specified during property registration.</span></span>  
  
 <span data-ttu-id="9a989-129">**X しないで**プロパティのアクセサーの依存関係プロパティの検証ロジックを配置します。</span><span class="sxs-lookup"><span data-stu-id="9a989-129">**X DO NOT** put dependency property validation logic in the property’s accessors.</span></span> <span data-ttu-id="9a989-130">代わりに、検証コールバックを渡す`DependencyProperty.Register`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="9a989-130">Instead, pass a validation callback to `DependencyProperty.Register` method.</span></span>  
  
## <a name="dependency-property-change-notifications"></a><span data-ttu-id="9a989-131">依存関係プロパティの変更通知</span><span class="sxs-lookup"><span data-stu-id="9a989-131">Dependency Property Change Notifications</span></span>  
 <span data-ttu-id="9a989-132">**X しないで**依存関係プロパティのアクセサーでの変更通知のロジックを実装します。</span><span class="sxs-lookup"><span data-stu-id="9a989-132">**X DO NOT** implement change notification logic in dependency property accessors.</span></span> <span data-ttu-id="9a989-133">依存関係プロパティを変更通知のコールバックを指定することによって処理するために使用する必要があります組み込みの変更通知機能があり、<xref:System.Windows.PropertyMetadata>です。</span><span class="sxs-lookup"><span data-stu-id="9a989-133">Dependency properties have a built-in change notifications feature that must be used by supplying a change notification callback to the <xref:System.Windows.PropertyMetadata>.</span></span>  
  
## <a name="dependency-property-value-coercion"></a><span data-ttu-id="9a989-134">依存関係プロパティの値の強制</span><span class="sxs-lookup"><span data-stu-id="9a989-134">Dependency Property Value Coercion</span></span>  
 <span data-ttu-id="9a989-135">プロパティの強制変換は、プロパティ ストアが実際に変更する前に、set アクセス操作子がプロパティ set アクセス操作子に渡された値が変更されたときに行われます。</span><span class="sxs-lookup"><span data-stu-id="9a989-135">Property coercion takes place when the value given to a property setter is modified by the setter before the property store is actually modified.</span></span>  
  
 <span data-ttu-id="9a989-136">**X しないで**依存関係プロパティのアクセサーに強制変換ロジックを実装します。</span><span class="sxs-lookup"><span data-stu-id="9a989-136">**X DO NOT** implement coercion logic in dependency property accessors.</span></span>  
  
 <span data-ttu-id="9a989-137">依存関係プロパティが、ビルトインの強制変換機能を持っているし、強制型変換のコールバックを指定することによって使用できます、`PropertyMetadata`です。</span><span class="sxs-lookup"><span data-stu-id="9a989-137">Dependency properties have a built-in coercion feature, and it can be used by supplying a coercion callback to the `PropertyMetadata`.</span></span>  
  
 <span data-ttu-id="9a989-138">*部分 © 2005、2009 Microsoft Corporation します。All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="9a989-138">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="9a989-139">*ピアソン教育, Inc. からのアクセス許可によって検出[Framework デザイン ガイドライン: 規則、表現方法、および再利用可能な .NET ライブラリを第 2 版パターン](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)は Cwalina と Brad Abrams、2008 年 10 月 22 日で発行されました。Microsoft Windows 開発シリーズの一部として、Addison-wesley Professional。*</span><span class="sxs-lookup"><span data-stu-id="9a989-139">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a989-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="9a989-140">See Also</span></span>  
 [<span data-ttu-id="9a989-141">フレームワーク デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="9a989-141">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="9a989-142">共通デザイン パターン</span><span class="sxs-lookup"><span data-stu-id="9a989-142">Common Design Patterns</span></span>](../../../docs/standard/design-guidelines/common-design-patterns.md)

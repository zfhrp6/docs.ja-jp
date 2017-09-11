---
title: "Visual Basic における名前空間 |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.global
dev_langs:
- VB
helpviewer_keywords:
- assemblies [Visual Basic], namespaces
- name collisions
- Global keyword [Visual Basic]
- namespace pollution
- names, avoiding conflicts
- naming conflicts, namespaces
- namespaces, assemblies
- Visual Basic code, namespaces
- fully qualified names
- naming conventions, naming conflicts
- namespaces
ms.assetid: cffac744-ab8c-4f1f-ba50-732c22ab4b88
caps.latest.revision: 27
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: bfc9f8f71b5ce5e05b6509ad490354663f894651
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="namespaces-in-visual-basic"></a><span data-ttu-id="25482-102">Visual Basic における名前空間</span><span class="sxs-lookup"><span data-stu-id="25482-102">Namespaces in Visual Basic</span></span>
<span data-ttu-id="25482-103">アセンブリ内で定義されているオブジェクトは、名前空間によって編成されています。</span><span class="sxs-lookup"><span data-stu-id="25482-103">Namespaces organize the objects defined in an assembly.</span></span> <span data-ttu-id="25482-104">アセンブリには複数の名前空間を含めることができます。さらに、名前空間の中に他の名前空間を含めることもできます。</span><span class="sxs-lookup"><span data-stu-id="25482-104">Assemblies can contain multiple namespaces, which can in turn contain other namespaces.</span></span> <span data-ttu-id="25482-105">名前空間を使用するとあいまいさがなくなるため、クラス ライブラリを使用する場合など、多数のオブジェクトを使用する場合に参照が簡単になります。</span><span class="sxs-lookup"><span data-stu-id="25482-105">Namespaces prevent ambiguity and simplify references when using large groups of objects such as class libraries.</span></span>  
  
 <span data-ttu-id="25482-106">たとえば、[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]を定義、<xref:System.Windows.Forms.ListBox>クラス、<xref:System.Windows.Forms?displayProperty=fullName>名前空間</xref:System.Windows.Forms?displayProperty=fullName></xref:System.Windows.Forms.ListBox>。</span><span class="sxs-lookup"><span data-stu-id="25482-106">For example, the [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] defines the <xref:System.Windows.Forms.ListBox> class in the <xref:System.Windows.Forms?displayProperty=fullName> namespace.</span></span> <span data-ttu-id="25482-107">次のコードは、このクラスの完全修飾名を使用して変数を宣言する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="25482-107">The following code fragment shows how to declare a variable using the fully qualified name for this class:</span></span>  
  
 <span data-ttu-id="25482-108">[!code-vb[VbVbalrApplication&6;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="25482-108">[!code-vb[VbVbalrApplication#6](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_1.vb)]</span></span>  
  
## <a name="avoiding-name-collisions"></a><span data-ttu-id="25482-109">名前の競合の回避</span><span class="sxs-lookup"><span data-stu-id="25482-109">Avoiding Name Collisions</span></span>  
 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]<span data-ttu-id="25482-110">名前空間とも呼ばれる問題に対処*名前空間の汚染*で別のライブラリでの類似した名前を使用してクラス ライブラリの開発者が妨げられます。</span><span class="sxs-lookup"><span data-stu-id="25482-110"> namespaces address a problem sometimes called *namespace pollution*, in which the developer of a class library is hampered by the use of similar names in another library.</span></span> <span data-ttu-id="25482-111">このような既存コンポーネントとの競合は、 *名前の競合*とも呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="25482-111">These conflicts with existing components are sometimes called *name collisions*.</span></span>  
  
 <span data-ttu-id="25482-112">たとえば、 `ListBox`という名前の新しいクラスを作成した場合、プロジェクト内ではこのクラスを修飾子を付けずに使用できます。</span><span class="sxs-lookup"><span data-stu-id="25482-112">For example, if you create a new class named `ListBox`, you can use it inside your project without qualification.</span></span> <span data-ttu-id="25482-113">ただし、使用する場合、 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] <xref:System.Windows.Forms.ListBox>クラス同じプロジェクト内の参照を一意にするための完全修飾参照を使用する必要があります</xref:System.Windows.Forms.ListBox>。</span><span class="sxs-lookup"><span data-stu-id="25482-113">However, if you want to use the [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] <xref:System.Windows.Forms.ListBox> class in the same project, you must use a fully qualified reference to make the reference unique.</span></span> <span data-ttu-id="25482-114">参照が一意でない場合、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] は、名前があいまいであることを示すエラーを生成します。</span><span class="sxs-lookup"><span data-stu-id="25482-114">If the reference is not unique, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] produces an error stating that the name is ambiguous.</span></span> <span data-ttu-id="25482-115">次のコード例では、これらのオブジェクトを宣言する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="25482-115">The following code example demonstrates how to declare these objects:</span></span>  
  
 <span data-ttu-id="25482-116">[!code-vb[VbVbalrApplication&#7;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="25482-116">[!code-vb[VbVbalrApplication#7](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_2.vb)]</span></span>  
  
 <span data-ttu-id="25482-117">次の図は、いずれも `ListBox`という名前のオブジェクトを持つ、2 つの名前空間の階層を表しています。</span><span class="sxs-lookup"><span data-stu-id="25482-117">The following illustration shows two namespace hierarchies, both containing an object named `ListBox`.</span></span>  
  
 <span data-ttu-id="25482-118">![Namespace 階層](../../../visual-basic/programming-guide/program-structure/media/vanamespacehierarchy.gif "vaNamespaceHierarchy")</span><span class="sxs-lookup"><span data-stu-id="25482-118">![Namespace Hierarchy](../../../visual-basic/programming-guide/program-structure/media/vanamespacehierarchy.gif "vaNamespaceHierarchy")</span></span>  
  
 <span data-ttu-id="25482-119">既定では、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] で作成するすべての実行可能ファイルには、プロジェクトと同名の名前空間が含まれます。</span><span class="sxs-lookup"><span data-stu-id="25482-119">By default, every executable file you create with [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] contains a namespace with the same name as your project.</span></span> <span data-ttu-id="25482-120">たとえば、 `ListBoxProject`という名前のプロジェクト内でオブジェクトを定義した場合、実行可能ファイル ListBoxProject.exe には `ListBoxProject`という名前空間が含まれます。</span><span class="sxs-lookup"><span data-stu-id="25482-120">For example, if you define an object within a project named `ListBoxProject`, the executable file ListBoxProject.exe contains a namespace called `ListBoxProject`.</span></span>  
  
 <span data-ttu-id="25482-121">複数のアセンブリで同じ名前空間を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="25482-121">Multiple assemblies can use the same namespace.</span></span> [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="25482-122"> はこれらを&1; つの名前セットとして扱います。</span><span class="sxs-lookup"><span data-stu-id="25482-122"> treats them as a single set of names.</span></span> <span data-ttu-id="25482-123">たとえば、`Assemb1` というアセンブリの `SomeNameSpace` という名前空間のクラスを定義した後に、`Assemb2` というアセンブリの同じ名前空間のクラスを定義できます。</span><span class="sxs-lookup"><span data-stu-id="25482-123">For example, you can define classes for a namespace called `SomeNameSpace` in an assembly named `Assemb1`, and define additional classes for the same namespace from an assembly named `Assemb2`.</span></span>  
  
## <a name="fully-qualified-names"></a><span data-ttu-id="25482-124">完全修飾名</span><span class="sxs-lookup"><span data-stu-id="25482-124">Fully Qualified Names</span></span>  
 <span data-ttu-id="25482-125">完全修飾名は、オブジェクトが定義されている名前空間の名前で始まるオブジェクト参照です。</span><span class="sxs-lookup"><span data-stu-id="25482-125">Fully qualified names are object references that are prefixed with the name of the namespace in which the object is defined.</span></span> <span data-ttu-id="25482-126">他のプロジェクトで定義されているオブジェクトを使用するには、 **[プロジェクト]** メニューの **[参照の追加]** をクリックしてそのクラスへの参照を作成し、コード内でそのオブジェクトの完全修飾名を使用します。</span><span class="sxs-lookup"><span data-stu-id="25482-126">You can use objects defined in other projects if you create a reference to the class (by choosing **Add Reference** from the **Project** menu) and then use the fully qualified name for the object in your code.</span></span> <span data-ttu-id="25482-127">次のコードは、別のプロジェクトの名前空間のオブジェクトを使用して完全修飾名を使用する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="25482-127">The following code fragment shows how to use the fully qualified name for an object from another project's namespace:</span></span>  
  
 <span data-ttu-id="25482-128">[!code-vb[VbVbalrApplication&#8;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="25482-128">[!code-vb[VbVbalrApplication#8](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_3.vb)]</span></span>  
  
 <span data-ttu-id="25482-129">完全修飾名を使用すると、どのオブジェクトを使用するかをコンパイラが認識できるため、名前の競合を防止できます。</span><span class="sxs-lookup"><span data-stu-id="25482-129">Fully qualified names prevent naming conflicts because they make it possible for the compiler to determine which object is being used.</span></span> <span data-ttu-id="25482-130">ただし、名前自体が長くなるため、使いにくくなります。</span><span class="sxs-lookup"><span data-stu-id="25482-130">However, the names themselves can get long and cumbersome.</span></span> <span data-ttu-id="25482-131">この問題を回避するには、 `Imports` ステートメントを使って *エイリアス*を定義します。エイリアスとは、完全修飾名の代わりに使用できる短い名前です。</span><span class="sxs-lookup"><span data-stu-id="25482-131">To get around this, you can use the `Imports` statement to define an *alias*—an abbreviated name you can use in place of a fully qualified name.</span></span> <span data-ttu-id="25482-132">たとえば、次のコード例では、2 つの完全修飾名に対してエイリアスを作成し、作成したエイリアスを使って&2; つのオブジェクトを定義しています。</span><span class="sxs-lookup"><span data-stu-id="25482-132">For example, the following code example creates aliases for two fully qualified names, and uses these aliases to define two objects.</span></span>  
  
 <span data-ttu-id="25482-133">[!code-vb[VbVbalrApplication&#9;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="25482-133">[!code-vb[VbVbalrApplication#9](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_4.vb)]</span></span>  
  
 <span data-ttu-id="25482-134">[!code-vb[VbVbalrApplication&#10;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="25482-134">[!code-vb[VbVbalrApplication#10](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_5.vb)]</span></span>  
  
 <span data-ttu-id="25482-135">エイリアスを指定せずに `Imports` ステートメントを使用すると、インポートした名前空間のすべての名前を修飾子を付けずに使用できます。ただし、それらの名前がプロジェクト内で一意であることが必要です。</span><span class="sxs-lookup"><span data-stu-id="25482-135">If you use the `Imports` statement without an alias, you can use all the names in that namespace without qualification, provided they are unique to the project.</span></span> <span data-ttu-id="25482-136">プロジェクトに、同じ名前の複数の項目を持つ名前空間をインポートする `Imports` ステートメントがある場合は、それらの名前を使用するときに完全修飾名を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="25482-136">If your project contains `Imports` statements for namespaces that contain items with the same name, you must fully qualify that name when you use it.</span></span> <span data-ttu-id="25482-137">たとえば、プロジェクトに次の&2; つの `Imports` ステートメントがあるとします。</span><span class="sxs-lookup"><span data-stu-id="25482-137">Suppose, for example, your project contained the following two `Imports` statements:</span></span>  
  
 <span data-ttu-id="25482-138">[!code-vb[VbVbalrApplication&#11;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="25482-138">[!code-vb[VbVbalrApplication#11](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_6.vb)]</span></span>  
  
 <span data-ttu-id="25482-139">この場合、完全修飾名を使わずに `Class1` を使おうとすると、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] から、`Class1` という名前があいまいであることを指摘するエラーが生成されます。</span><span class="sxs-lookup"><span data-stu-id="25482-139">If you attempt to use `Class1` without fully qualifying it, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] produces an error stating that the name `Class1` is ambiguous.</span></span>  
  
## <a name="namespace-level-statements"></a><span data-ttu-id="25482-140">名前空間レベルのステートメント</span><span class="sxs-lookup"><span data-stu-id="25482-140">Namespace Level Statements</span></span>  
 <span data-ttu-id="25482-141">名前空間内では、モジュール、インターフェイス、クラス、デリゲート、列挙体、構造体、他の名前空間などの項目を定義できます。</span><span class="sxs-lookup"><span data-stu-id="25482-141">Within a namespace, you can define items such as modules, interfaces, classes, delegates, enumerations, structures, and other namespaces.</span></span> <span data-ttu-id="25482-142">プロパティ、プロシージャ、変数、イベントなどの項目を名前空間のレベルで定義することはできません。</span><span class="sxs-lookup"><span data-stu-id="25482-142">You cannot define items such as properties, procedures, variables and events at the namespace level.</span></span> <span data-ttu-id="25482-143">これらの項目は、モジュール、構造体、クラスなどのコンテナー内で宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="25482-143">These items must be declared within containers such as modules, structures, or classes.</span></span>  
  
## <a name="global-keyword-in-fully-qualified-names"></a><span data-ttu-id="25482-144">完全修飾名の Global キーワード</span><span class="sxs-lookup"><span data-stu-id="25482-144">Global Keyword in Fully Qualified Names</span></span>  
 <span data-ttu-id="25482-145">その階層内のコードがへのアクセスをブロックされている名前空間の入れ子になった階層を定義している場合、 <xref:System?displayProperty=fullName>.NET Framework の名前空間</xref:System?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="25482-145">If you have defined a nested hierarchy of namespaces, code inside that hierarchy might be blocked from accessing the <xref:System?displayProperty=fullName> namespace of the .NET Framework.</span></span> <span data-ttu-id="25482-146">次の例では、階層を`SpecialSpace.System` <xref:System?displayProperty=fullName>.</xref:System?displayProperty=fullName>へのアクセスをブロックの名前空間</span><span class="sxs-lookup"><span data-stu-id="25482-146">The following example illustrates a hierarchy in which the `SpecialSpace.System` namespace blocks access to <xref:System?displayProperty=fullName>.</span></span>  
  
```vb  
Namespace SpecialSpace  
    Namespace System  
        Class abc  
            Function getValue() As System.Int32  
                Dim n As System.Int32  
                Return n  
            End Function  
        End Class  
    End Namespace  
End Namespace  
```  
  
 <span data-ttu-id="25482-147">その結果、Visual Basic コンパイラにはへの参照が解決できない正常に<xref:System.Int32?displayProperty=fullName>ので、`SpecialSpace.System`が定義されていません`Int32`</xref:System.Int32?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="25482-147">As a result, the Visual Basic compiler cannot successfully resolve the reference to <xref:System.Int32?displayProperty=fullName>, because `SpecialSpace.System` does not define `Int32`.</span></span> <span data-ttu-id="25482-148">`Global` キーワードを使用すると、修飾チェーンを .NET Framework クラス ライブラリの最も外側のレベルで開始できます。</span><span class="sxs-lookup"><span data-stu-id="25482-148">You can use the `Global` keyword to start the qualification chain at the outermost level of the .NET Framework class library.</span></span> <span data-ttu-id="25482-149">これによりを指定する、<xref:System?displayProperty=fullName>名前空間またはクラス ライブラリの他の名前空間</xref:System?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="25482-149">This allows you to specify the <xref:System?displayProperty=fullName> namespace or any other namespace in the class library.</span></span> <span data-ttu-id="25482-150">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="25482-150">The following example illustrates this.</span></span>  
  
```vb  
Namespace SpecialSpace  
    Namespace System  
        Class abc  
            Function getValue() As Global.System.Int32  
                Dim n As Global.System.Int32  
                Return n  
            End Function  
        End Class  
    End Namespace  
End Namespace  
```  
  
 <span data-ttu-id="25482-151">使用することができます`Global`などにアクセスする他のルート レベルの名前空間<xref:Microsoft.VisualBasic?displayProperty=fullName>、およびプロジェクトに関連付けられている任意の名前空間</xref:Microsoft.VisualBasic?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="25482-151">You can use `Global` to access other root-level namespaces, such as <xref:Microsoft.VisualBasic?displayProperty=fullName>, and any namespace associated with your project.</span></span>  
  
## <a name="global-keyword-in-namespace-statements"></a><span data-ttu-id="25482-152">名前空間のステートメントでの Global キーワード</span><span class="sxs-lookup"><span data-stu-id="25482-152">Global Keyword in Namespace Statements</span></span>  
 <span data-ttu-id="25482-153">使用することも、`Global`のキーワード、 [Namespace ステートメント](../../../visual-basic/language-reference/statements/namespace-statement.md)します。</span><span class="sxs-lookup"><span data-stu-id="25482-153">You can also use the `Global` keyword in a [Namespace Statement](../../../visual-basic/language-reference/statements/namespace-statement.md).</span></span> <span data-ttu-id="25482-154">これにより、プロジェクトのルート名前空間から名前空間を定義できます。</span><span class="sxs-lookup"><span data-stu-id="25482-154">This lets you define a namespace out of the root namespace of your project.</span></span>  
  
 <span data-ttu-id="25482-155">プロジェクト内のすべての名前空間は、プロジェクトのルート名前空間に基づいています。</span><span class="sxs-lookup"><span data-stu-id="25482-155">All namespaces in your project are based on the root namespace for the project.</span></span>  <span data-ttu-id="25482-156">Visual Studio では、プロジェクト内のすべてのコードで、既定のルート名前空間としてプロジェクト名が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="25482-156">Visual Studio assigns your project name as the default root namespace for all code in your project.</span></span> <span data-ttu-id="25482-157">たとえば、プロジェクト名が `ConsoleApplication1`である場合、そのプログラミング要素は `ConsoleApplication1`名前空間に属します。</span><span class="sxs-lookup"><span data-stu-id="25482-157">For example, if your project is named `ConsoleApplication1`, its programming elements belong to namespace `ConsoleApplication1`.</span></span> <span data-ttu-id="25482-158">`Namespace Magnetosphere`を宣言すると、プロジェクトの `Magnetosphere` への参照は `ConsoleApplication1.Magnetosphere`にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="25482-158">If you declare `Namespace Magnetosphere`, references to `Magnetosphere` in the project will access `ConsoleApplication1.Magnetosphere`.</span></span>  
  
 <span data-ttu-id="25482-159">次の例では、プロジェクトのルート名前空間から名前空間を宣言するために `Global` キーワードを使用しています。</span><span class="sxs-lookup"><span data-stu-id="25482-159">The following examples use the `Global` keyword to declare a namespace out of the root namespace for the project.</span></span>  
  
 <span data-ttu-id="25482-160">[!code-vb[VbVbalrApplication #&22;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_7.vb)]</span><span class="sxs-lookup"><span data-stu-id="25482-160">[!code-vb[VbVbalrApplication#22](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_7.vb)]</span></span>  
  
 <span data-ttu-id="25482-161">名前空間宣言では、 `Global` を別の名前空間に入れ子にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="25482-161">In a namespace declaration, `Global` cannot be nested in another namespace.</span></span>  
  
 <span data-ttu-id="25482-162">使用することができます、[アプリケーション ページで、プロジェクト デザイナー) (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/application-page-project-designer-visual-basic)を表示および変更、**ルート Namespace**プロジェクトのです。</span><span class="sxs-lookup"><span data-stu-id="25482-162">You can use the [Application Page, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/application-page-project-designer-visual-basic) to view and modify the **Root Namespace** of the project.</span></span>  <span data-ttu-id="25482-163">新しいプロジェクトの場合、 **ルート名前空間** の既定値は、プロジェクト名です。</span><span class="sxs-lookup"><span data-stu-id="25482-163">For new projects, the **Root Namespace** defaults to the project name.</span></span> <span data-ttu-id="25482-164">`Global` を最上位レベルの名前空間にするには、 **ルート名前空間** のエントリを消去して、ボックスを空にします。</span><span class="sxs-lookup"><span data-stu-id="25482-164">To cause `Global` to be the top-level namespace, you can clear the **Root Namespace** entry so that the box is empty.</span></span> <span data-ttu-id="25482-165">**ルート名前空間** を消去すると、名前空間の宣言で `Global` キーワードの必要がなくなります。</span><span class="sxs-lookup"><span data-stu-id="25482-165">Clearing **Root Namespace** removes the need for the `Global` keyword in namespace declarations.</span></span>  
  
 <span data-ttu-id="25482-166">`Namespace` ステートメントで .NET framework の名前空間にもなっている名前を宣言する場合、 `Global` キーワードが完全修飾名で使用されていない場合、.NET Framework 名前空間は使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="25482-166">If a `Namespace` statement declares a name that is also a namespace in the .NET Framework, the .NET Framework namespace becomes unavailable if the `Global` keyword is not used in a fully qualified name.</span></span> <span data-ttu-id="25482-167">`Global` キーワードを使用せずに、.NET Framework 名前空間へのアクセスを有効にするには、 `Global` キーワードを `Namespace` ステートメントに含めます。</span><span class="sxs-lookup"><span data-stu-id="25482-167">To enable access to that .NET Framework namespace without using the `Global` keyword, you can include the `Global` keyword in the `Namespace` statement.</span></span>  
  
 <span data-ttu-id="25482-168">次の例では、 `Global` 名前空間の宣言で、 `System.Text` キーワードを使用しています。</span><span class="sxs-lookup"><span data-stu-id="25482-168">The following example has the `Global` keyword in the `System.Text` namespace declaration.</span></span>  
  
 <span data-ttu-id="25482-169">場合、`Global`キーワードが名前空間宣言に存在しなかった<xref:System.Text.StringBuilder>を指定せずにアクセスできませんでした`Global.System.Text.StringBuilder`</xref:System.Text.StringBuilder>。</span><span class="sxs-lookup"><span data-stu-id="25482-169">If the `Global` keyword was not present in the namespace declaration, <xref:System.Text.StringBuilder> could not be accessed without specifying `Global.System.Text.StringBuilder`.</span></span> <span data-ttu-id="25482-170">`ConsoleApplication1`という名前のプロジェクトで、 `System.Text` キーワードが使用されていない場合、 `ConsoleApplication1.System.Text` を参照すると、 `Global` にアクセスすることになります。</span><span class="sxs-lookup"><span data-stu-id="25482-170">For a project named `ConsoleApplication1`, references to `System.Text` would access `ConsoleApplication1.System.Text` if the `Global` keyword was not used.</span></span>  
  
 <span data-ttu-id="25482-171">[!code-vb[VbVbalrApplication #&21;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_8.vb)]</span><span class="sxs-lookup"><span data-stu-id="25482-171">[!code-vb[VbVbalrApplication#21](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_8.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25482-172">関連項目</span><span class="sxs-lookup"><span data-stu-id="25482-172">See Also</span></span>  
 <span data-ttu-id="25482-173"><xref:System.Windows.Forms.ListBox></xref:System.Windows.Forms.ListBox></span><span class="sxs-lookup"><span data-stu-id="25482-173"><xref:System.Windows.Forms.ListBox></span></span>   
 <span data-ttu-id="25482-174"><xref:System.Windows.Forms?displayProperty=fullName></xref:System.Windows.Forms?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="25482-174"><xref:System.Windows.Forms?displayProperty=fullName></span></span>   
<span data-ttu-id="25482-175"> [アセンブリとグローバル アセンブリ キャッシュ](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md) </span><span class="sxs-lookup"><span data-stu-id="25482-175"> [Assemblies and the Global Assembly Cache](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md) </span></span>  
<span data-ttu-id="25482-176"> [方法: を作成し、コマンドラインを使用してアセンブリを使用します。](http://msdn.microsoft.com/library/70f65026-3687-4e9c-ab79-c18b97dd8be4) </span><span class="sxs-lookup"><span data-stu-id="25482-176"> [How to: Create and Use Assemblies Using the Command Line](http://msdn.microsoft.com/library/70f65026-3687-4e9c-ab79-c18b97dd8be4) </span></span>  
<span data-ttu-id="25482-177"> [参照と Imports ステートメント](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md) </span><span class="sxs-lookup"><span data-stu-id="25482-177"> [References and the Imports Statement](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md) </span></span>  
<span data-ttu-id="25482-178"> [Imports ステートメント (.NET 名前空間および型)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) </span><span class="sxs-lookup"><span data-stu-id="25482-178"> [Imports Statement (.NET Namespace and Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) </span></span>  
<span data-ttu-id="25482-179"> [Office ソリューションのコードの記述](https://msdn.microsoft.com/library/bb608596)</span><span class="sxs-lookup"><span data-stu-id="25482-179"> [Writing Code in Office Solutions](https://msdn.microsoft.com/library/bb608596)</span></span>

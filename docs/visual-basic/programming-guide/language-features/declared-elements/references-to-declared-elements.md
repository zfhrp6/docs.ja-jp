---
title: "宣言された要素 (Visual Basic) への参照 |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- declared elements
- references, declared elements
- qualified names
ms.assetid: d6301709-f4cc-4b7a-b8ba-80898f14ab46
caps.latest.revision: 19
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
ms.openlocfilehash: 5de39ac5c30b1cff2a8bfd0cd606dee33c078514
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="references-to-declared-elements-visual-basic"></a><span data-ttu-id="89b9c-102">宣言された要素の参照 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="89b9c-102">References to Declared Elements (Visual Basic)</span></span>
<span data-ttu-id="89b9c-103">コードが宣言された要素を参照している場合、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]コンパイラでその名前の適切な宣言への参照を名前に一致します。</span><span class="sxs-lookup"><span data-stu-id="89b9c-103">When your code refers to a declared element, the [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler matches the name in your reference to the appropriate declaration of that name.</span></span> <span data-ttu-id="89b9c-104">参照にはそれらの要素を制御するには複数の要素が同じ名前で宣言されている場合*正規*の名前。</span><span class="sxs-lookup"><span data-stu-id="89b9c-104">If more than one element is declared with the same name, you can control which of those elements is to be referenced by *qualifying* its name.</span></span>  
  
 <span data-ttu-id="89b9c-105">コンパイラが名の宣言でへの参照を名前に一致しようとした場合、*だけ狭いスコープ*します。</span><span class="sxs-lookup"><span data-stu-id="89b9c-105">The compiler attempts to match a name reference to a name declaration with the *narrowest scope*.</span></span> <span data-ttu-id="89b9c-106">これは、参照するコードから開始して、下位レベルの要素を含む外側はことを意味します。</span><span class="sxs-lookup"><span data-stu-id="89b9c-106">This means it starts with the code making the reference and works outward through successive levels of containing elements.</span></span>  
  
 <span data-ttu-id="89b9c-107">次の例では、同じ名前の&2; つの変数への参照を示します。</span><span class="sxs-lookup"><span data-stu-id="89b9c-107">The following example shows references to two variables with the same name.</span></span> <span data-ttu-id="89b9c-108">例では、2 つの変数を宣言して、各名前付き`totalCount`、モジュール内でスコープのさまざまなレベルで`container`します。</span><span class="sxs-lookup"><span data-stu-id="89b9c-108">The example declares two variables, each named `totalCount`, at different levels of scope in module `container`.</span></span> <span data-ttu-id="89b9c-109">ときにプロシージャ`showCount`表示`totalCount`修飾なし、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]コンパイラが最も狭いスコープ、つまり内でローカル宣言を使用して宣言への参照を解決`showCount`します。</span><span class="sxs-lookup"><span data-stu-id="89b9c-109">When the procedure `showCount` displays `totalCount` without qualification, the [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler resolves the reference to the declaration with the narrowest scope, namely the local declaration inside `showCount`.</span></span> <span data-ttu-id="89b9c-110">適用されるときに`totalCount`を含むモジュールを使用して`container`コンパイラがより広いスコープを使用して宣言への参照を解決します。</span><span class="sxs-lookup"><span data-stu-id="89b9c-110">When it qualifies `totalCount` with the containing module `container`, the compiler resolves the reference to the declaration with the broader scope.</span></span>  
  
```vb  
' Assume these two modules are both in the same assembly.  
Module container  
    Public totalCount As Integer = 1  
    Public Sub showCount()  
        Dim totalCount As Integer = 6000  
        ' The following statement displays the local totalCount (6000).  
        MsgBox("Unqualified totalCount is " & CStr(totalCount))  
        ' The following statement displays the module's totalCount (1).  
        MsgBox("container.totalCount is " & CStr(container.totalCount))  
    End Sub  
End Module  
Module callingModule  
    Public Sub displayCount()  
        container.showCount()  
        ' The following statement displays the containing module's totalCount (1).  
        MsgBox("container.totalCount is " & CStr(container.totalCount))  
    End Sub  
End Module  
```  
  
## <a name="qualifying-an-element-name"></a><span data-ttu-id="89b9c-111">要素名の修飾</span><span class="sxs-lookup"><span data-stu-id="89b9c-111">Qualifying an Element Name</span></span>  
 <span data-ttu-id="89b9c-112">この検索処理をオーバーライドし、名前で宣言されているより広いスコープする必要がありますを指定する場合*修飾*より広いスコープのコンテナー要素の名前。</span><span class="sxs-lookup"><span data-stu-id="89b9c-112">If you want to override this search process and specify a name declared in a broader scope, you must *qualify* the name with the containing element of the broader scope.</span></span> <span data-ttu-id="89b9c-113">場合によっては、コンテナーの要素を修飾する必要がありますも。</span><span class="sxs-lookup"><span data-stu-id="89b9c-113">In some cases, you might also have to qualify the containing element.</span></span>  
  
 <span data-ttu-id="89b9c-114">ターゲット要素を定義する場所を識別する情報、ソース ステートメント内の前の名前を修飾します。</span><span class="sxs-lookup"><span data-stu-id="89b9c-114">Qualifying a name means preceding it in your source statement with information that identifies where the target element is defined.</span></span> <span data-ttu-id="89b9c-115">この情報と呼ばれる、*修飾文字列*します。</span><span class="sxs-lookup"><span data-stu-id="89b9c-115">This information is called a *qualification string*.</span></span> <span data-ttu-id="89b9c-116">1 つを含めることまたは複数の名前空間とモジュールの場合、クラスまたは構造体します。</span><span class="sxs-lookup"><span data-stu-id="89b9c-116">It can include one or more namespaces and a module, class, or structure.</span></span>  
  
 <span data-ttu-id="89b9c-117">修飾文字列は、モジュール、クラス、または対象の要素を含む構造体に明確を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="89b9c-117">The qualification string should unambiguously specify the module, class, or structure containing the target element.</span></span> <span data-ttu-id="89b9c-118">コンテナーは、他のコンテナー要素、通常は名前空間に存在するさらに可能性があります。</span><span class="sxs-lookup"><span data-stu-id="89b9c-118">The container might in turn be located in another containing element, usually a namespace.</span></span> <span data-ttu-id="89b9c-119">修飾文字列に含まれるいくつかの要素を含める必要がある可能性があります。</span><span class="sxs-lookup"><span data-stu-id="89b9c-119">You might need to include several containing elements in the qualification string.</span></span>  
  
#### <a name="to-access-a-declared-element-by-qualifying-its-name"></a><span data-ttu-id="89b9c-120">その名前を修飾することによって宣言された要素にアクセスするには</span><span class="sxs-lookup"><span data-stu-id="89b9c-120">To access a declared element by qualifying its name</span></span>  
  
1.  <span data-ttu-id="89b9c-121">要素が定義されている場所を決定します。</span><span class="sxs-lookup"><span data-stu-id="89b9c-121">Determine the location in which the element has been defined.</span></span> <span data-ttu-id="89b9c-122">これは、名前空間または名前空間の階層も含まれます。</span><span class="sxs-lookup"><span data-stu-id="89b9c-122">This might include a namespace, or even a hierarchy of namespaces.</span></span> <span data-ttu-id="89b9c-123">最下位レベルの名前空間内では、モジュール、クラスまたは構造体の要素を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="89b9c-123">Within the lowest-level namespace, the element must be contained in a module, class, or structure.</span></span>  
  
    ```vb  
    ' Assume the following hierarchy exists outside your code.  
    Namespace outerSpace  
        Namespace innerSpace  
            Module holdsTotals  
                Public Structure totals  
                    Public thisTotal As Integer  
                    Public Shared grandTotal As Long  
                End Structure  
            End Module  
        End Namespace  
    End Namespace  
    ```  
  
2.  <span data-ttu-id="89b9c-124">ターゲット要素の場所に基づいて修飾パスを決定します。</span><span class="sxs-lookup"><span data-stu-id="89b9c-124">Determine a qualification path based on the target element's location.</span></span> <span data-ttu-id="89b9c-125">最上位レベルの名前空間を持つ起動、最下位レベルの名前空間に進み、モジュール、クラス、または対象の要素を含む構造体で終了します。</span><span class="sxs-lookup"><span data-stu-id="89b9c-125">Start with the highest-level namespace, proceed to the lowest-level namespace, and end with the module, class, or structure containing the target element.</span></span> <span data-ttu-id="89b9c-126">パス内の各要素には、それに続く要素を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="89b9c-126">Each element in the path must contain the element that follows it.</span></span>  
  
     <span data-ttu-id="89b9c-127">`outerSpace` → `innerSpace` → `holdsTotals` → `totals`</span><span class="sxs-lookup"><span data-stu-id="89b9c-127">`outerSpace` → `innerSpace` → `holdsTotals` → `totals`</span></span>  
  
3.  <span data-ttu-id="89b9c-128">ターゲット要素の修飾文字列を準備します。</span><span class="sxs-lookup"><span data-stu-id="89b9c-128">Prepare the qualification string for the target element.</span></span> <span data-ttu-id="89b9c-129">ピリオドを挿入 (`.`) のパスのすべての要素の後です。</span><span class="sxs-lookup"><span data-stu-id="89b9c-129">Place a period (`.`) after every element in the path.</span></span> <span data-ttu-id="89b9c-130">アプリケーションによっては、修飾文字列内のすべての要素へのアクセスが必要です。</span><span class="sxs-lookup"><span data-stu-id="89b9c-130">Your application must have access to every element in your qualification string.</span></span>  
  
    ```vb  
    outerSpace.innerSpace.holdsTotals.totals.  
    ```  
  
4.  <span data-ttu-id="89b9c-131">式または通常の方法で対象となる要素を参照する代入ステートメントを記述します。</span><span class="sxs-lookup"><span data-stu-id="89b9c-131">Write the expression or assignment statement referring to the target element in the normal way.</span></span>  
  
    ```vb  
    grandTotal = 9000  
    ```  
  
5.  <span data-ttu-id="89b9c-132">修飾文字列とターゲットの要素名の前に記述します。</span><span class="sxs-lookup"><span data-stu-id="89b9c-132">Precede the target element name with the qualification string.</span></span> <span data-ttu-id="89b9c-133">名前は、ピリオドの直後 (`.`) モジュール、クラス、または、要素を格納する構造体を参照します。</span><span class="sxs-lookup"><span data-stu-id="89b9c-133">The name should immediately follow the period (`.`) that follows the module, class, or structure that contains the element.</span></span>  
  
    ```vb  
    ' Assume the following module is part of your code.  
    Module accessGrandTotal  
        Public Sub setGrandTotal()  
            outerSpace.innerSpace.holdsTotals.totals.grandTotal = 9000  
        End Sub  
    End Module  
    ```  
  
6.  <span data-ttu-id="89b9c-134">コンパイラでは、修飾文字列を使用して、ターゲット要素の参照と一致させて、明確に明確な宣言を見つけます。</span><span class="sxs-lookup"><span data-stu-id="89b9c-134">The compiler uses the qualification string to find a clear, unambiguous declaration to which it can match the target element reference.</span></span>  
  
 <span data-ttu-id="89b9c-135">アプリケーションに同じ名前を持つ&2; つ以上のプログラミング要素へのアクセスがある場合は、名前の参照を修飾することもあります。</span><span class="sxs-lookup"><span data-stu-id="89b9c-135">You might also have to qualify a name reference if your application has access to more than one programming element that has the same name.</span></span> <span data-ttu-id="89b9c-136">たとえば、<xref:System.Windows.Forms>と<xref:System.Web.UI.WebControls>両方名前空間を含む、`Label`クラス (<xref:System.Windows.Forms.Label?displayProperty=fullName>と<xref:System.Web.UI.WebControls.Label?displayProperty=fullName>).</xref:System.Web.UI.WebControls.Label?displayProperty=fullName> </xref:System.Windows.Forms.Label?displayProperty=fullName> </xref:System.Web.UI.WebControls> </xref:System.Windows.Forms></span><span class="sxs-lookup"><span data-stu-id="89b9c-136">For example, the <xref:System.Windows.Forms> and <xref:System.Web.UI.WebControls> namespaces both contain a `Label` class (<xref:System.Windows.Forms.Label?displayProperty=fullName> and <xref:System.Web.UI.WebControls.Label?displayProperty=fullName>).</span></span> <span data-ttu-id="89b9c-137">アプリケーションは、両方を使用している場合、またはそれ自体を定義する`Label`クラス、さまざまなを区別する必要があります`Label`オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="89b9c-137">If your application uses both, or if it defines its own `Label` class, you must distinguish the different `Label` objects.</span></span> <span data-ttu-id="89b9c-138">変数の宣言には、名前空間またはインポート エイリアスを含めます。</span><span class="sxs-lookup"><span data-stu-id="89b9c-138">Include the namespace or import alias in the variable declaration.</span></span> <span data-ttu-id="89b9c-139">次の例では、インポート エイリアスを使用します。</span><span class="sxs-lookup"><span data-stu-id="89b9c-139">The following example uses the import alias.</span></span>  
  
```vb  
' The following statement must precede all your declarations.  
Imports win = System.Windows.Forms, web = System.Web.UI.WebControls  
' The following statement references the Windows.Forms.Label class.  
Dim winLabel As New win.Label()  
```  
  
## <a name="members-of-other-containing-elements"></a><span data-ttu-id="89b9c-140">別のコンテナー要素のメンバー</span><span class="sxs-lookup"><span data-stu-id="89b9c-140">Members of Other Containing Elements</span></span>  
 <span data-ttu-id="89b9c-141">別のクラスまたは構造体の非共有メンバーを使用する場合は、最初に変数またはクラスまたは構造体のインスタンスを指す式でメンバー名を修飾する必要があります。</span><span class="sxs-lookup"><span data-stu-id="89b9c-141">When you use a nonshared member of another class or structure, you must first qualify the member name with a variable or expression that points to an instance of the class or structure.</span></span> <span data-ttu-id="89b9c-142">次の例で`demoClass`という名前のクラスのインスタンスは、`class1`です。</span><span class="sxs-lookup"><span data-stu-id="89b9c-142">In the following example, `demoClass` is an instance of a class named `class1`.</span></span>  
  
```vb  
Dim demoClass As class1 = New class1()  
demoClass.someSub[(argumentlist)]  
```  
  
 <span data-ttu-id="89b9c-143">クラス名自体を使用していないメンバーを修飾することはできません[Shared](../../../../visual-basic/language-reference/modifiers/shared.md)します。</span><span class="sxs-lookup"><span data-stu-id="89b9c-143">You cannot use the class name itself to qualify a member that is not [Shared](../../../../visual-basic/language-reference/modifiers/shared.md).</span></span> <span data-ttu-id="89b9c-144">まず、オブジェクト変数のインスタンスを作成する必要があります (ここで`demoClass`) それを変数名で参照します。</span><span class="sxs-lookup"><span data-stu-id="89b9c-144">You must first create an instance in an object variable (in this case `demoClass`) and then reference it by the variable name.</span></span>  
  
 <span data-ttu-id="89b9c-145">クラスまたは構造体がある場合、`Shared`メンバー、またはいずれかでクラスまたは構造体の名前の変数またはインスタンスを指す式には、そのメンバーを修飾することができます。</span><span class="sxs-lookup"><span data-stu-id="89b9c-145">If a class or structure has a `Shared` member, you can qualify that member either with the class or structure name or with a variable or expression that points to an instance.</span></span>  
  
 <span data-ttu-id="89b9c-146">モジュールには、個別のインスタンスはありませんし、そのすべてのメンバーが`Shared`既定です。</span><span class="sxs-lookup"><span data-stu-id="89b9c-146">A module does not have any separate instances, and all its members are `Shared` by default.</span></span> <span data-ttu-id="89b9c-147">そのため、モジュール名を持つモジュール メンバーを修飾します。</span><span class="sxs-lookup"><span data-stu-id="89b9c-147">Therefore, you qualify a module member with the module name.</span></span>  
  
 <span data-ttu-id="89b9c-148">次の例では、モジュール メンバー プロシージャへの修飾参照を示します。</span><span class="sxs-lookup"><span data-stu-id="89b9c-148">The following example shows qualified references to module member procedures.</span></span> <span data-ttu-id="89b9c-149">2 つの例`Sub`という名前の手順、`perform`プロジェクト内の異なるモジュールでします。</span><span class="sxs-lookup"><span data-stu-id="89b9c-149">The example declares two `Sub` procedures, both named `perform`, in different modules in a project.</span></span> <span data-ttu-id="89b9c-150">1 つずつでは、独自のモジュール内の修飾なしで指定できますが、それ以外の任意の場所から参照されている場合に限定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="89b9c-150">Each one can be specified without qualification within its own module but must be qualified if referenced from anywhere else.</span></span> <span data-ttu-id="89b9c-151">最後を参照するため`module3`修飾していない`perform`コンパイラは、その参照を解決できません。</span><span class="sxs-lookup"><span data-stu-id="89b9c-151">Because the final reference in `module3` does not qualify `perform`, the compiler cannot resolve that reference.</span></span>  
  
```vb  
' Assume these three modules are all in the same assembly.  
Module module1  
    Public Sub perform()  
        MsgBox("module1.perform() now returning")  
    End Sub  
End Module  
Module module2  
    Public Sub perform()  
        MsgBox("module2.perform() now returning")  
    End Sub  
    Public Sub doSomething()  
        ' The following statement calls perform in module2, the active module.  
        perform()  
        ' The following statement calls perform in module1.  
        module1.perform()  
    End Sub  
End Module  
Module module3  
    Public Sub callPerform()  
        ' The following statement calls perform in module1.  
        module1.perform()  
        ' The following statement makes an unresolvable name reference  
        ' and therefore generates a COMPILER ERROR.  
        perform() ' INVALID statement  
    End Sub  
End Module  
```  
  
## <a name="references-to-projects"></a><span data-ttu-id="89b9c-152">プロジェクトへの参照</span><span class="sxs-lookup"><span data-stu-id="89b9c-152">References to Projects</span></span>  
 <span data-ttu-id="89b9c-153">使用する[パブリック](../../../../visual-basic/language-reference/modifiers/public.md)、別のプロジェクトで定義されている要素は、まず設定、*参照*そのプロジェクトのアセンブリやタイプ ライブラリにします。</span><span class="sxs-lookup"><span data-stu-id="89b9c-153">To use [Public](../../../../visual-basic/language-reference/modifiers/public.md) elements defined in another project, you must first set a *reference* to that project's assembly or type library.</span></span> <span data-ttu-id="89b9c-154">参照を設定する をクリックして**参照の追加**上、**プロジェクト** メニュー、 [/reference (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/reference.md)コマンド ライン コンパイラ オプション。</span><span class="sxs-lookup"><span data-stu-id="89b9c-154">To set a reference, click **Add Reference** on the **Project** menu, or use the [/reference (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/reference.md) command-line compiler option.</span></span>  
  
 <span data-ttu-id="89b9c-155">XML オブジェクト モデルを使用するなど、[!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="89b9c-155">For example, you can use the XML object model of the [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)].</span></span> <span data-ttu-id="89b9c-156">参照を設定した場合、<xref:System.Xml>名前空間を宣言して<xref:System.Xml.XmlDocument>.</xref:System.Xml.XmlDocument>など、そのクラスのいずれかを使用する</xref:System.Xml></span><span class="sxs-lookup"><span data-stu-id="89b9c-156">If you set a reference to the <xref:System.Xml> namespace, you can declare and use any of its classes, such as <xref:System.Xml.XmlDocument>.</span></span> <span data-ttu-id="89b9c-157">次のコードの例では、 <xref:System.Xml.XmlDocument>。</xref:System.Xml.XmlDocument></span><span class="sxs-lookup"><span data-stu-id="89b9c-157">The following example uses <xref:System.Xml.XmlDocument>.</span></span>  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As System.Xml.XmlDocument  
```  
  
## <a name="importing-containing-elements"></a><span data-ttu-id="89b9c-158">コンテナー要素のインポート</span><span class="sxs-lookup"><span data-stu-id="89b9c-158">Importing Containing Elements</span></span>  
 <span data-ttu-id="89b9c-159">使用することができます、 [Imports ステートメント (.NET Namespace よぶ型)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)に*インポート*モジュールまたはを使用するクラスを含む名前空間。</span><span class="sxs-lookup"><span data-stu-id="89b9c-159">You can use the [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) to *import* the namespaces that contain the modules or classes that you want to use.</span></span> <span data-ttu-id="89b9c-160">これにより、その名前を完全に修飾せずにインポートされた名前空間で定義された要素を参照してください。</span><span class="sxs-lookup"><span data-stu-id="89b9c-160">This enables you to refer to the elements defined in an imported namespace without fully qualifying their names.</span></span> <span data-ttu-id="89b9c-161">次の例は、インポートする前の例を書き換える、<xref:System.Xml>名前空間</xref:System.Xml>。</span><span class="sxs-lookup"><span data-stu-id="89b9c-161">The following example rewrites the previous example to import the <xref:System.Xml> namespace.</span></span>  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement must precede all your declarations.  
Imports System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As XmlDocument  
```  
  
 <span data-ttu-id="89b9c-162">さらに、`Imports`ステートメントで定義できる、*インポート エイリアス*インポートされた名前空間ごとにします。</span><span class="sxs-lookup"><span data-stu-id="89b9c-162">In addition, the `Imports` statement can define an *import alias* for each imported namespace.</span></span> <span data-ttu-id="89b9c-163">これにより、ソース コード短く、読みやすくします。</span><span class="sxs-lookup"><span data-stu-id="89b9c-163">This can make the source code shorter and easier to read.</span></span> <span data-ttu-id="89b9c-164">次の例を使用する前の例を書き換える`xD`のエイリアスとして、<xref:System.Xml>名前空間</xref:System.Xml>。</span><span class="sxs-lookup"><span data-stu-id="89b9c-164">The following example rewrites the previous example to use `xD` as an alias for the <xref:System.Xml> namespace.</span></span>  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement must precede all your declarations.  
Imports xD = System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As xD.XmlDocument  
```  
  
 <span data-ttu-id="89b9c-165">`Imports`ステートメントは行いません要素が他のプロジェクトからアプリケーションに使用します。</span><span class="sxs-lookup"><span data-stu-id="89b9c-165">The `Imports` statement does not make elements from other projects available to your application.</span></span> <span data-ttu-id="89b9c-166">つまり、参照を設定場所は考慮しません。</span><span class="sxs-lookup"><span data-stu-id="89b9c-166">That is, it does not take the place of setting a reference.</span></span> <span data-ttu-id="89b9c-167">だけに、名前空間をインポートするには、その名前空間で定義されている名前を修飾するための要件を削除します。</span><span class="sxs-lookup"><span data-stu-id="89b9c-167">Importing a namespace just removes the requirement to qualify the names defined in that namespace.</span></span>  
  
 <span data-ttu-id="89b9c-168">使用することも、`Imports`モジュール、クラス、構造体、および列挙型をインポートするステートメントです。</span><span class="sxs-lookup"><span data-stu-id="89b9c-168">You can also use the `Imports` statement to import modules, classes, structures, and enumerations.</span></span> <span data-ttu-id="89b9c-169">このようなインポートされた要素の修飾なしのメンバーを使用して送信することができます。</span><span class="sxs-lookup"><span data-stu-id="89b9c-169">You can then use the members of such imported elements without qualification.</span></span> <span data-ttu-id="89b9c-170">ただし、クラスと構造体は、変数またはクラスまたは構造体のインスタンスに評価される式の非共有メンバーを常に修飾する必要があります。</span><span class="sxs-lookup"><span data-stu-id="89b9c-170">However, you must always qualify nonshared members of classes and structures with a variable or expression that evaluates to an instance of the class or structure.</span></span>  
  
## <a name="naming-guidelines"></a><span data-ttu-id="89b9c-171">名前付けのガイドライン</span><span class="sxs-lookup"><span data-stu-id="89b9c-171">Naming Guidelines</span></span>  
 <span data-ttu-id="89b9c-172">同じ名前を持つ&2; つ以上のプログラミング要素を定義するとき、*あいまいさという名前を*コンパイラがその名前への参照を解決しようとすると発生することができます。</span><span class="sxs-lookup"><span data-stu-id="89b9c-172">When you define two or more programming elements that have the same name, a *name ambiguity* can result when the compiler attempts to resolve a reference to that name.</span></span> <span data-ttu-id="89b9c-173">1 つの定義がスコープ内にある数より多い場合、または、参照が解決されない定義がスコープでない場合は、です。</span><span class="sxs-lookup"><span data-stu-id="89b9c-173">If more than one definition is in scope, or if no definition is in scope, the reference is irresolvable.</span></span> <span data-ttu-id="89b9c-174">たとえば、このページで「修飾参照の使用例」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="89b9c-174">For an example, see "Qualified Reference Example" on this Help page.</span></span>  
  
 <span data-ttu-id="89b9c-175">すべての要素に一意の名前を提供することにより、名前のあいまいさを回避できます。</span><span class="sxs-lookup"><span data-stu-id="89b9c-175">You can avoid name ambiguity by giving all your elements unique names.</span></span> <span data-ttu-id="89b9c-176">その名の名前空間、モジュール、またはクラスを修飾しなくても任意の要素への参照をすることができます。</span><span class="sxs-lookup"><span data-stu-id="89b9c-176">Then you can make reference to any element without having to qualify its name with a namespace, module, or class.</span></span> <span data-ttu-id="89b9c-177">正しくない要素を誤って参照する可能性を低くします。</span><span class="sxs-lookup"><span data-stu-id="89b9c-177">You also reduce the chances of accidentally referring to the wrong element.</span></span>  
  
## <a name="shadowing"></a><span data-ttu-id="89b9c-178">シャドウ</span><span class="sxs-lookup"><span data-stu-id="89b9c-178">Shadowing</span></span>  
 <span data-ttu-id="89b9c-179">2 つのプログラミング要素は、同じ名前を共有する場合の&1; つ非表示にできます、または*シャドウ*、もう&1; つです。</span><span class="sxs-lookup"><span data-stu-id="89b9c-179">When two programming elements share the same name, one of them can hide, or *shadow*, the other one.</span></span> <span data-ttu-id="89b9c-180">影付きの要素は参照できません。代わりに、コードが影付きの要素名を使用する場合、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]コンパイラでは、それを解決する要素。</span><span class="sxs-lookup"><span data-stu-id="89b9c-180">A shadowed element is not available for reference; instead, when your code uses the shadowed element name, the [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler resolves it to the shadowing element.</span></span> <span data-ttu-id="89b9c-181">例と詳細については、次を参照してください。 [Visual Basic におけるシャドウ](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)します。</span><span class="sxs-lookup"><span data-stu-id="89b9c-181">For a more detailed explanation with examples, see [Shadowing in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89b9c-182">関連項目</span><span class="sxs-lookup"><span data-stu-id="89b9c-182">See Also</span></span>  
 <span data-ttu-id="89b9c-183">[宣言された要素名](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md) </span><span class="sxs-lookup"><span data-stu-id="89b9c-183">[Declared Element Names](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md) </span></span>  
<span data-ttu-id="89b9c-184"> [宣言された要素の特性](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md) </span><span class="sxs-lookup"><span data-stu-id="89b9c-184"> [Declared Element Characteristics](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md) </span></span>  
<span data-ttu-id="89b9c-185"> [NIB 方法: プロジェクトのプロパティと構成設定の変更](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67) </span><span class="sxs-lookup"><span data-stu-id="89b9c-185"> [NIB How to: Modify Project Properties and Configuration Settings](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67) </span></span>  
<span data-ttu-id="89b9c-186"> [変数](../../../../visual-basic/programming-guide/language-features/variables/index.md) </span><span class="sxs-lookup"><span data-stu-id="89b9c-186"> [Variables](../../../../visual-basic/programming-guide/language-features/variables/index.md) </span></span>  
<span data-ttu-id="89b9c-187"> [Imports ステートメント (.NET 名前空間および型)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) </span><span class="sxs-lookup"><span data-stu-id="89b9c-187"> [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) </span></span>  
<span data-ttu-id="89b9c-188"> [New 演算子](../../../../visual-basic/language-reference/operators/new-operator.md) </span><span class="sxs-lookup"><span data-stu-id="89b9c-188"> [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) </span></span>  
<span data-ttu-id="89b9c-189"> [Public](../../../../visual-basic/language-reference/modifiers/public.md)</span><span class="sxs-lookup"><span data-stu-id="89b9c-189"> [Public](../../../../visual-basic/language-reference/modifiers/public.md)</span></span>

---
title: 列挙型と名前修飾 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], enumerations
- Imports statement [Visual Basic], namespace declarations
- declaring namespaces [Visual Basic], enumerations
- name collisions
- ambiguous names [Visual Basic], enumerations
- enumerations [Visual Basic], name qualification
- names [Visual Basic], avoiding conflicts
- namespaces [Visual Basic], declaring
- naming conflicts, enumerations
- naming conflicts, qualifying names
- declaring enumerations
- references [Visual Basic], enumeration members
- naming conventions [Visual Basic], naming conflicts
- declarations [Visual Basic], namespaces
ms.assetid: 08ba2738-df52-4140-bc55-f57c871c9b73
ms.openlocfilehash: eb1f5653d968e81168833cd57813219e8f049b70
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648581"
---
# <a name="enumerations-and-name-qualification-visual-basic"></a><span data-ttu-id="ae532-102">列挙型と名前修飾 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ae532-102">Enumerations and Name Qualification (Visual Basic)</span></span>
<span data-ttu-id="ae532-103">通常、列挙体のメンバーを指す場合は、列挙型の名前でメンバー名を修飾する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ae532-103">Normally, when referring to a member of an enumeration, you must qualify the member name with the enumeration name.</span></span> <span data-ttu-id="ae532-104">例についてを参照する、`Sunday`のメンバー、`Days`列挙型では、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="ae532-104">For example, to refer to the `Sunday` member of your `Days` enumeration, you would use the following syntax:</span></span>  
  
 [!code-vb[VbEnumsTask#18](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_1.vb)]  
  
## <a name="using-the-imports-statement"></a><span data-ttu-id="ae532-105">Imports ステートメントを使用</span><span class="sxs-lookup"><span data-stu-id="ae532-105">Using the Imports Statement</span></span>  
 <span data-ttu-id="ae532-106">完全修飾名を使用して追加することで回避することができます、`Imports`名前空間の宣言セクションに次の例のように、コードのステートメント。</span><span class="sxs-lookup"><span data-stu-id="ae532-106">You can avoid using fully qualified names by adding an `Imports` statement to the namespace declarations section of your code, as in the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#22](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_2.vb)]  
  
 <span data-ttu-id="ae532-107">`Imports`ステートメントは参照先のプロジェクトおよびアセンブリからと内から名前空間の名前をインポート、ステートメントが表示されるモジュールと同じプロジェクトです。</span><span class="sxs-lookup"><span data-stu-id="ae532-107">An `Imports` statement imports namespace names from referenced projects and assemblies and from within the same project as the module in which the statement appears.</span></span> <span data-ttu-id="ae532-108">このステートメントが追加されると、次の例のように、修飾なしの列挙メンバーに参照できます。</span><span class="sxs-lookup"><span data-stu-id="ae532-108">Once this statement is added, you can refer to your enumeration members without qualification, as in the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#24](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_3.vb)]  
  
 <span data-ttu-id="ae532-109">列挙体に関連する定数のセットを整理するには、別のコンテキストで同じ定数名を使用できます。</span><span class="sxs-lookup"><span data-stu-id="ae532-109">By organizing sets of related constants in enumerations, you can use the same constant names in different contexts.</span></span> <span data-ttu-id="ae532-110">たとえば、同じ名前に、平日定数を使用することができます、`Days`と`WorkDays`列挙体です。</span><span class="sxs-lookup"><span data-stu-id="ae532-110">For example, you can use the same names for the weekday constants in the `Days` and `WorkDays` enumerations.</span></span> <span data-ttu-id="ae532-111">使用する場合、`Imports`列挙型でステートメントでは、する必要がありますあいまいな参照を回避するように注意します。</span><span class="sxs-lookup"><span data-stu-id="ae532-111">If you use the `Imports` statement with your enumerations, you must be careful to avoid ambiguous references.</span></span> <span data-ttu-id="ae532-112">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="ae532-112">Consider the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#22](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_2.vb)]  
  
 [!code-vb[VbEnumsTask#25](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_4.vb)]  
  
 <span data-ttu-id="ae532-113">想定される`Monday`両方のメンバーである、`Days`列挙と`Workdays`列挙型、このコードはコンパイラ エラーが生成されます。</span><span class="sxs-lookup"><span data-stu-id="ae532-113">Assuming that `Monday` is a member of both the `Days` enumeration and the `Workdays` enumeration, this code generates a compiler error.</span></span> <span data-ttu-id="ae532-114">あいまいな参照を避けるためには、定数を個別に参照するとき、するには、その列挙体で定数名を修飾します。</span><span class="sxs-lookup"><span data-stu-id="ae532-114">To avoid ambiguous references when referring to an individual constant, qualify the constant name with its enumeration.</span></span> <span data-ttu-id="ae532-115">次のコードを指す、`Saturday`内の定数、`Days`と`WorkDays`列挙体です。</span><span class="sxs-lookup"><span data-stu-id="ae532-115">The following code refers to the `Saturday` constants in the `Days` and `WorkDays` enumerations.</span></span>  
  
 [!code-vb[VbEnumsTask#32](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_5.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="ae532-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="ae532-116">See Also</span></span>  
 [<span data-ttu-id="ae532-117">定数と列挙体</span><span class="sxs-lookup"><span data-stu-id="ae532-117">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)  
 [<span data-ttu-id="ae532-118">方法: 列挙型を宣言</span><span class="sxs-lookup"><span data-stu-id="ae532-118">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)  
 [<span data-ttu-id="ae532-119">方法 : 列挙型のメンバーを参照する</span><span class="sxs-lookup"><span data-stu-id="ae532-119">How to: Refer to an Enumeration Member</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)  
 [<span data-ttu-id="ae532-120">方法: Visual Basic で列挙型を反復処理します。</span><span class="sxs-lookup"><span data-stu-id="ae532-120">How to: Iterate Through An Enumeration in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)  
 [<span data-ttu-id="ae532-121">方法 : 列挙値に関連付けられている文字列を確認する</span><span class="sxs-lookup"><span data-stu-id="ae532-121">How to: Determine the String Associated with an Enumeration Value</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)  
 [<span data-ttu-id="ae532-122">列挙型を使用する状況</span><span class="sxs-lookup"><span data-stu-id="ae532-122">When to Use an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)  
 [<span data-ttu-id="ae532-123">定数とリテラルのデータ型</span><span class="sxs-lookup"><span data-stu-id="ae532-123">Constant and Literal Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)  
 [<span data-ttu-id="ae532-124">Enum ステートメント</span><span class="sxs-lookup"><span data-stu-id="ae532-124">Enum Statement</span></span>](../../../../visual-basic/language-reference/statements/enum-statement.md)  
 [<span data-ttu-id="ae532-125">Imports ステートメント (.NET 名前空間および型)</span><span class="sxs-lookup"><span data-stu-id="ae532-125">Imports Statement (.NET Namespace and Type)</span></span>](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [<span data-ttu-id="ae532-126">データの種類</span><span class="sxs-lookup"><span data-stu-id="ae532-126">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/data-type-summary.md)

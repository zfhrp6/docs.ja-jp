---
title: GetType 演算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.GetType
helpviewer_keywords:
- GetType operator [Visual Basic]
- GetType keyword [Visual Basic]
ms.assetid: 4f733297-2503-4607-850c-15eba65fff90
ms.openlocfilehash: 581f576222eb149aede841a5da7a0e5f38c77b58
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603848"
---
# <a name="gettype-operator-visual-basic"></a><span data-ttu-id="f004e-102">GetType 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f004e-102">GetType Operator (Visual Basic)</span></span>
<span data-ttu-id="f004e-103">返します、<xref:System.Type>指定した型のオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="f004e-103">Returns a <xref:System.Type> object for the specified type.</span></span> <span data-ttu-id="f004e-104"><xref:System.Type>オブジェクトなど、そのプロパティ、メソッド、およびイベントの種類に関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="f004e-104">The <xref:System.Type> object provides information about the type such as its properties, methods, and events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f004e-105">構文</span><span class="sxs-lookup"><span data-stu-id="f004e-105">Syntax</span></span>  
  
```  
GetType(typename)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f004e-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f004e-106">Parameters</span></span>  
  
|<span data-ttu-id="f004e-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f004e-107">Parameter</span></span>|<span data-ttu-id="f004e-108">説明</span><span class="sxs-lookup"><span data-stu-id="f004e-108">Description</span></span>|  
|---|---|  
|`typename`|<span data-ttu-id="f004e-109">情報を取得する型の名前。</span><span class="sxs-lookup"><span data-stu-id="f004e-109">The name of the type for which you desire information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f004e-110">コメント</span><span class="sxs-lookup"><span data-stu-id="f004e-110">Remarks</span></span>  
 <span data-ttu-id="f004e-111">`GetType`演算子を返します、 <xref:System.Type> 、指定されたオブジェクト`typename`です。</span><span class="sxs-lookup"><span data-stu-id="f004e-111">The `GetType` operator returns the <xref:System.Type> object for the specified `typename`.</span></span> <span data-ttu-id="f004e-112">定義済みのすべての種類の名前を渡すことができます`typename`です。</span><span class="sxs-lookup"><span data-stu-id="f004e-112">You can pass the name of any defined type in `typename`.</span></span> <span data-ttu-id="f004e-113">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="f004e-113">This includes the following:</span></span>  
  
-   <span data-ttu-id="f004e-114">Visual Basic データ型など`Boolean`または`Date`です。</span><span class="sxs-lookup"><span data-stu-id="f004e-114">Any Visual Basic data type, such as `Boolean` or `Date`.</span></span>  
  
-   <span data-ttu-id="f004e-115">.NET Framework クラス、構造体、モジュール、または、インターフェイスなど<xref:System.ArgumentException?displayProperty=nameWithType>または<xref:System.Double?displayProperty=nameWithType>です。</span><span class="sxs-lookup"><span data-stu-id="f004e-115">Any .NET Framework class, structure, module, or interface, such as <xref:System.ArgumentException?displayProperty=nameWithType> or <xref:System.Double?displayProperty=nameWithType>.</span></span>  
  
-   <span data-ttu-id="f004e-116">クラス、構造体、モジュール、またはアプリケーションで定義されているインターフェイス。</span><span class="sxs-lookup"><span data-stu-id="f004e-116">Any class, structure, module, or interface defined by your application.</span></span>  
  
-   <span data-ttu-id="f004e-117">アプリケーションで定義されている任意の配列。</span><span class="sxs-lookup"><span data-stu-id="f004e-117">Any array defined by your application.</span></span>  
  
-   <span data-ttu-id="f004e-118">アプリケーションで定義されている任意のデリゲート。</span><span class="sxs-lookup"><span data-stu-id="f004e-118">Any delegate defined by your application.</span></span>  
  
-   <span data-ttu-id="f004e-119">Visual Basic、.NET Framework、またはアプリケーションによって定義された任意の列挙体です。</span><span class="sxs-lookup"><span data-stu-id="f004e-119">Any enumeration defined by Visual Basic, the .NET Framework, or your application.</span></span>  
  
 <span data-ttu-id="f004e-120">オブジェクト変数の型のオブジェクトを取得する場合は、使用、<xref:System.Type.GetType%2A?displayProperty=nameWithType>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="f004e-120">If you want to get the type object of an object variable, use the <xref:System.Type.GetType%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="f004e-121">`GetType`演算子は、次の状況で役に立ちます。</span><span class="sxs-lookup"><span data-stu-id="f004e-121">The `GetType` operator can be useful in the following circumstances:</span></span>  
  
-   <span data-ttu-id="f004e-122">型のメタデータは、実行時にアクセスする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f004e-122">You must access the metadata for a type at run time.</span></span> <span data-ttu-id="f004e-123"><xref:System.Type>オブジェクトは型のメンバーと配置の情報などのメタデータを提供します。</span><span class="sxs-lookup"><span data-stu-id="f004e-123">The <xref:System.Type> object supplies metadata such as type members and deployment information.</span></span> <span data-ttu-id="f004e-124">必要に、たとえば、アセンブリを反映するようになります。</span><span class="sxs-lookup"><span data-stu-id="f004e-124">You need this, for example, to reflect over an assembly.</span></span> <span data-ttu-id="f004e-125">詳細については、「<xref:System.Reflection?displayProperty=nameWithType>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f004e-125">For more information, see <xref:System.Reflection?displayProperty=nameWithType>.</span></span>  
  
-   <span data-ttu-id="f004e-126">同じ型のインスタンスを参照しているかどうかを次の 2 つのオブジェクト参照を比較するには。</span><span class="sxs-lookup"><span data-stu-id="f004e-126">You want to compare two object references to see if they refer to instances of the same type.</span></span> <span data-ttu-id="f004e-127">場合は、`GetType`同じへの参照を返します<xref:System.Type>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="f004e-127">If they do, `GetType` returns references to the same <xref:System.Type> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f004e-128">例</span><span class="sxs-lookup"><span data-stu-id="f004e-128">Example</span></span>  
 <span data-ttu-id="f004e-129">次の例、`GetType`演算子を使用します。</span><span class="sxs-lookup"><span data-stu-id="f004e-129">The following examples show the `GetType` operator in use.</span></span>  
  
 [!code-vb[VbVbalrOperators#26](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/gettype-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="f004e-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="f004e-130">See Also</span></span>  
 [<span data-ttu-id="f004e-131">Visual Basic における演算子の優先順位</span><span class="sxs-lookup"><span data-stu-id="f004e-131">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="f004e-132">機能別の演算子一覧</span><span class="sxs-lookup"><span data-stu-id="f004e-132">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="f004e-133">演算子および式</span><span class="sxs-lookup"><span data-stu-id="f004e-133">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)

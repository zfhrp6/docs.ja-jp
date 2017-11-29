---
title: "DLL 関数を保持するクラスの作成"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- COM interop, DLL functions
- unmanaged functions
- COM interop, platform invoke
- interoperation with unmanaged code, DLL functions
- interoperation with unmanaged code, platform invoke
- platform invoke, creating class for functions
- DLL functions
ms.assetid: e08e4c34-0223-45f7-aa55-a3d8dd979b0f
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ac3c3542e46168f5903ff0425740a29f16253733
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="creating-a-class-to-hold-dll-functions"></a><span data-ttu-id="1d8fa-102">DLL 関数を保持するクラスの作成</span><span class="sxs-lookup"><span data-stu-id="1d8fa-102">Creating a Class to Hold DLL Functions</span></span>
<span data-ttu-id="1d8fa-103">マネージ クラス内の頻繁に使用される DLL 関数をラップすることは、プラットフォームの機能をカプセル化するための効果的な方法です。</span><span class="sxs-lookup"><span data-stu-id="1d8fa-103">Wrapping a frequently used DLL function in a managed class is an effective approach to encapsulate platform functionality.</span></span> <span data-ttu-id="1d8fa-104">これはすべてのケースで必須であるわけではありませんが、DLL 関数の定義には手間がかかり、エラーが発生しやすくなるため、クラス ラッパーを用意しておくと便利です。</span><span class="sxs-lookup"><span data-stu-id="1d8fa-104">Although it is not mandatory to do so in every case, providing a class wrapper is convenient because defining DLL functions can be cumbersome and error-prone.</span></span> <span data-ttu-id="1d8fa-105">Visual Basic や C# でプログラミングしている場合は、DLL 関数をクラスまたは Visual Basic モジュール内で宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1d8fa-105">If you are programming in Visual Basic or C#, you must declare DLL functions within a class or Visual Basic module.</span></span>  
  
 <span data-ttu-id="1d8fa-106">クラス内では、呼び出す DLL 関数ごとに静的メソッドを定義します。</span><span class="sxs-lookup"><span data-stu-id="1d8fa-106">Within a class, you define a static method for each DLL function you want to call.</span></span> <span data-ttu-id="1d8fa-107">この定義には、メソッド引数を渡すときに使用される呼び出し規則や文字セットなどの追加情報を含めることができます。この情報を省略すると、既定の設定が選択されます。</span><span class="sxs-lookup"><span data-stu-id="1d8fa-107">The definition can include additional information, such as the character set or the calling convention used in passing method arguments; by omitting this information, you select the default settings.</span></span> <span data-ttu-id="1d8fa-108">宣言のオプションと、既定の設定の完全なリストについては、「[Creating Prototypes in Managed Code](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)」(マネージ コードでのプロトタイプの作成) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1d8fa-108">For a complete list of declaration options and their default settings, see [Creating Prototypes in Managed Code](../../../docs/framework/interop/creating-prototypes-in-managed-code.md).</span></span>  
  
 <span data-ttu-id="1d8fa-109">ラッピングが完了すると、他の静的関数でメソッドを呼び出す場合と同じように、関数でメソッドを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="1d8fa-109">Once wrapped, you can call methods on the function as you call methods on any other static function.</span></span> <span data-ttu-id="1d8fa-110">プラットフォーム呼び出しでは、基になるエクスポートされた関数が自動的に処理されます。</span><span class="sxs-lookup"><span data-stu-id="1d8fa-110">Platform invoke handles the underlying exported function automatically.</span></span>  
  
 <span data-ttu-id="1d8fa-111">プラットフォーム呼び出しのためにマネージ クラスをデザインする場合は、クラスと DLL 関数との関係を考慮してください。</span><span class="sxs-lookup"><span data-stu-id="1d8fa-111">When designing a managed class for platform invoke, consider the relationships between classes and DLL functions.</span></span> <span data-ttu-id="1d8fa-112">たとえば、次のように操作できます。</span><span class="sxs-lookup"><span data-stu-id="1d8fa-112">For example, you can:</span></span>  
  
-   <span data-ttu-id="1d8fa-113">既存のクラス内で DLL 関数を宣言する。</span><span class="sxs-lookup"><span data-stu-id="1d8fa-113">Declare DLL functions within an existing class.</span></span>  
  
-   <span data-ttu-id="1d8fa-114">関数を分離し、検索しやすくするために、DLL 関数ごとに別のクラスを作成する。</span><span class="sxs-lookup"><span data-stu-id="1d8fa-114">Create an individual class for each DLL function, keeping functions isolated and easy to find.</span></span>  
  
-   <span data-ttu-id="1d8fa-115">論理的なグループを形成し、オーバーヘッドを減らすため、一連の関連する DLL 関数に対して 1 つのクラスを作成する。</span><span class="sxs-lookup"><span data-stu-id="1d8fa-115">Create one class for a set of related DLL functions to form logical groupings and reduce overhead.</span></span>  
  
 <span data-ttu-id="1d8fa-116">クラスおよびそのメソッドには、任意の名前を付けることができます。</span><span class="sxs-lookup"><span data-stu-id="1d8fa-116">You can name the class and its methods as you please.</span></span> <span data-ttu-id="1d8fa-117">プラットフォーム呼び出しで使用する .NET ベースの宣言を作成する方法を示す例については、「[プラットフォーム呼び出しによるデータのマーシャリング](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1d8fa-117">For examples that demonstrate how to construct .NET-based declarations to be used with platform invoke, see [Marshaling Data with Platform Invoke](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d8fa-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="1d8fa-118">See Also</span></span>  
 [<span data-ttu-id="1d8fa-119">アンマネージ DLL 関数の処理</span><span class="sxs-lookup"><span data-stu-id="1d8fa-119">Consuming Unmanaged DLL Functions</span></span>](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)  
 [<span data-ttu-id="1d8fa-120">DLL 内の関数の識別</span><span class="sxs-lookup"><span data-stu-id="1d8fa-120">Identifying Functions in DLLs</span></span>](../../../docs/framework/interop/identifying-functions-in-dlls.md)  
 [<span data-ttu-id="1d8fa-121">マネージ コードでのプロトタイプの作成</span><span class="sxs-lookup"><span data-stu-id="1d8fa-121">Creating Prototypes in Managed Code</span></span>](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)  
 [<span data-ttu-id="1d8fa-122">DLL 関数の呼び出し</span><span class="sxs-lookup"><span data-stu-id="1d8fa-122">Calling a DLL Function</span></span>](../../../docs/framework/interop/calling-a-dll-function.md)

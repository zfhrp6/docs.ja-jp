---
title: '方法: プロシージャの複数のバージョンを定義する (Visual Basic)'
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
- procedure overloading [Visual Basic], multiple versions
ms.assetid: 71ccdd66-1b00-4b66-bee4-6926c0d696f4
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e6db075e9b31355d4a0a593040b1fe7c96a0c730
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-define-multiple-versions-of-a-procedure-visual-basic"></a><span data-ttu-id="f89a8-102">方法: プロシージャの複数のバージョンを定義する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f89a8-102">How to: Define Multiple Versions of a Procedure (Visual Basic)</span></span>
<span data-ttu-id="f89a8-103">によって複数のバージョンのプロシージャを定義できます*オーバー ロード*バージョンごとに異なるパラメーター リストは、同じ名前を使用しています。</span><span class="sxs-lookup"><span data-stu-id="f89a8-103">You can define a procedure in multiple versions by *overloading* it, using the same name but a different parameter list for each version.</span></span> <span data-ttu-id="f89a8-104">オーバー ロードの目的では、名前で区別することがなく密接に関連するいくつかのバージョンのプロシージャを定義します。</span><span class="sxs-lookup"><span data-stu-id="f89a8-104">The purpose of overloading is to define several closely related versions of a procedure without having to differentiate them by name.</span></span>  
  
 <span data-ttu-id="f89a8-105">詳細については、次を参照してください。[プロシージャのオーバー ロード](./procedure-overloading.md)です。</span><span class="sxs-lookup"><span data-stu-id="f89a8-105">For more information, see [Procedure Overloading](./procedure-overloading.md).</span></span>  
  
### <a name="to-define-multiple-versions-of-a-procedure"></a><span data-ttu-id="f89a8-106">プロシージャの複数のバージョンを定義するには</span><span class="sxs-lookup"><span data-stu-id="f89a8-106">To define multiple versions of a procedure</span></span>  
  
1.  <span data-ttu-id="f89a8-107">書き込み、`Sub`または`Function`を定義する手順の各バージョンの宣言ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="f89a8-107">Write a `Sub` or `Function` declaration statement for each version of the procedure you want to define.</span></span> <span data-ttu-id="f89a8-108">すべての宣言で同じプロシージャ名を使用します。</span><span class="sxs-lookup"><span data-stu-id="f89a8-108">Use the same procedure name in every declaration.</span></span>  
  
2.  <span data-ttu-id="f89a8-109">前に、`Sub`または`Function`を含む各宣言でキーワード、 [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md)キーワード。</span><span class="sxs-lookup"><span data-stu-id="f89a8-109">Precede the `Sub` or `Function` keyword in each declaration with the [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) keyword.</span></span> <span data-ttu-id="f89a8-110">省略可能`Overloads`宣言のいずれかに含める場合は、宣言に含める必要がありますすべての宣言でします。</span><span class="sxs-lookup"><span data-stu-id="f89a8-110">You can optionally omit `Overloads` in the declarations, but if you include it in any of the declarations, you must include it in every declaration.</span></span>  
  
3.  <span data-ttu-id="f89a8-111">次の各宣言ステートメントには、呼び出し元のコードがそのバージョンのパラメーター リストに一致する引数を指定する、特定のケースを処理する手順のコードを記述します。</span><span class="sxs-lookup"><span data-stu-id="f89a8-111">Following each declaration statement, write procedure code to handle the specific case where the calling code supplies arguments matching that version's parameter list.</span></span> <span data-ttu-id="f89a8-112">必要はありませんをテストする呼び出し元のコードが提供するパラメーターです。</span><span class="sxs-lookup"><span data-stu-id="f89a8-112">You do not have to test for which parameters the calling code has supplied.</span></span> <span data-ttu-id="f89a8-113">Visual Basic では、プロシージャの対応するバージョンに制御を渡します。</span><span class="sxs-lookup"><span data-stu-id="f89a8-113">Visual Basic passes control to the matching version of your procedure.</span></span>  
  
4.  <span data-ttu-id="f89a8-114">使用してプロシージャの各バージョンの終了、`End Sub`または`End Function`に応じてステートメントです。</span><span class="sxs-lookup"><span data-stu-id="f89a8-114">Terminate each version of the procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f89a8-115">例</span><span class="sxs-lookup"><span data-stu-id="f89a8-115">Example</span></span>  
 <span data-ttu-id="f89a8-116">次の例では定義、`Sub`顧客の残高に対してトランザクションをポストするプロシージャ。</span><span class="sxs-lookup"><span data-stu-id="f89a8-116">The following example defines a `Sub` procedure to post a transaction against a customer's balance.</span></span> <span data-ttu-id="f89a8-117">使用して、`Overloads`して名前と、他のアカウント番号によって、顧客が使用できるプロシージャの 2 つのバージョンを定義するキーワードです。</span><span class="sxs-lookup"><span data-stu-id="f89a8-117">It uses the `Overloads` keyword to define two versions of the procedure, one that accepts the customer by name and the other by account number.</span></span>  
  
 [!code-vb[VbVbcnProcedures#72](./codesnippet/VisualBasic/how-to-define-multiple-versions-of-a-procedure_1.vb)]  
  
 <span data-ttu-id="f89a8-118">呼び出し元のコードは、いずれかとして、顧客 id を取得できます、`String`または`Integer`、およびどちらの場合、同じ呼び出し元ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="f89a8-118">The calling code can obtain the customer identification as either a `String` or an `Integer`, and then use the same calling statement in either case.</span></span>  
  
 <span data-ttu-id="f89a8-119">これらのバージョンを呼び出す方法については、`post`プロシージャを参照してください[する方法: オーバー ロードされたプロシージャを呼び出す](./how-to-call-an-overloaded-procedure.md)です。</span><span class="sxs-lookup"><span data-stu-id="f89a8-119">For information on how to call these versions of the `post` procedure, see [How to: Call an Overloaded Procedure](./how-to-call-an-overloaded-procedure.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f89a8-120">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="f89a8-120">Compiling the Code</span></span>  
 <span data-ttu-id="f89a8-121">プロシージャ名が同じで、異なるパラメーター リストを持つ、オーバー ロードされたバージョンを確認します。</span><span class="sxs-lookup"><span data-stu-id="f89a8-121">Make sure each of your overloaded versions has the same procedure name but a different parameter list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f89a8-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="f89a8-122">See Also</span></span>  
 [<span data-ttu-id="f89a8-123">手順</span><span class="sxs-lookup"><span data-stu-id="f89a8-123">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="f89a8-124">プロシージャのパラメーターと引数</span><span class="sxs-lookup"><span data-stu-id="f89a8-124">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="f89a8-125">プロシージャのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="f89a8-125">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)  
 [<span data-ttu-id="f89a8-126">方法 : 省略可能なパラメーターを受け取るプロシージャをオーバーロードする</span><span class="sxs-lookup"><span data-stu-id="f89a8-126">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)  
 [<span data-ttu-id="f89a8-127">方法 : 不特定数のパラメーターを受け取るプロシージャをオーバーロードする</span><span class="sxs-lookup"><span data-stu-id="f89a8-127">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)  
 [<span data-ttu-id="f89a8-128">プロシージャのオーバーロードに関する注意事項</span><span class="sxs-lookup"><span data-stu-id="f89a8-128">Considerations in Overloading Procedures</span></span>](./considerations-in-overloading-procedures.md)  
 [<span data-ttu-id="f89a8-129">オーバーロードの解決</span><span class="sxs-lookup"><span data-stu-id="f89a8-129">Overload Resolution</span></span>](./overload-resolution.md)

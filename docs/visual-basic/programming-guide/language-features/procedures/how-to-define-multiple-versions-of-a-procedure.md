---
title: "方法: プロシージャ (Visual Basic) の複数のバージョンを定義する |Microsoft ドキュメント"
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
- procedures, defining
- Visual Basic code, procedures
- procedures, overloading
- procedures, multiple versions
- procedure overloading, multiple versions
ms.assetid: 71ccdd66-1b00-4b66-bee4-6926c0d696f4
caps.latest.revision: 14
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
ms.openlocfilehash: f4296ba3a78316b70011bcca18f7071716f3c90d
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-define-multiple-versions-of-a-procedure-visual-basic"></a><span data-ttu-id="a697c-102">方法: プロシージャの複数のバージョンを定義する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a697c-102">How to: Define Multiple Versions of a Procedure (Visual Basic)</span></span>
<span data-ttu-id="a697c-103">プロシージャを定義するには、複数のバージョンで*オーバー ロード*バージョンごとに異なるパラメーター リストは、同じ名前を使用しています。</span><span class="sxs-lookup"><span data-stu-id="a697c-103">You can define a procedure in multiple versions by *overloading* it, using the same name but a different parameter list for each version.</span></span> <span data-ttu-id="a697c-104">オーバー ロードの目的では、名前で区別することがなく密接に関連するいくつかのバージョンのプロシージャを定義します。</span><span class="sxs-lookup"><span data-stu-id="a697c-104">The purpose of overloading is to define several closely related versions of a procedure without having to differentiate them by name.</span></span>  
  
 <span data-ttu-id="a697c-105">詳細については、次を参照してください。[プロシージャのオーバー ロード](./procedure-overloading.md)します。</span><span class="sxs-lookup"><span data-stu-id="a697c-105">For more information, see [Procedure Overloading](./procedure-overloading.md).</span></span>  
  
### <a name="to-define-multiple-versions-of-a-procedure"></a><span data-ttu-id="a697c-106">プロシージャの複数のバージョンを定義するには</span><span class="sxs-lookup"><span data-stu-id="a697c-106">To define multiple versions of a procedure</span></span>  
  
1.  <span data-ttu-id="a697c-107">書き込み、`Sub`または`Function`を定義する手順の各バージョンの宣言ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="a697c-107">Write a `Sub` or `Function` declaration statement for each version of the procedure you want to define.</span></span> <span data-ttu-id="a697c-108">すべての宣言では、同じプロシージャ名を使用します。</span><span class="sxs-lookup"><span data-stu-id="a697c-108">Use the same procedure name in every declaration.</span></span>  
  
2.  <span data-ttu-id="a697c-109">前に、`Sub`または`Function`各宣言でキーワード、[オーバー ロード](../../../../visual-basic/language-reference/modifiers/overloads.md)キーワードです。</span><span class="sxs-lookup"><span data-stu-id="a697c-109">Precede the `Sub` or `Function` keyword in each declaration with the [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) keyword.</span></span> <span data-ttu-id="a697c-110">省略可能`Overloads`宣言のいずれかに含める場合は、宣言にする必要がありますに含めるすべての宣言です。</span><span class="sxs-lookup"><span data-stu-id="a697c-110">You can optionally omit `Overloads` in the declarations, but if you include it in any of the declarations, you must include it in every declaration.</span></span>  
  
3.  <span data-ttu-id="a697c-111">次の各宣言ステートメントには、呼び出し元のコードがそのバージョンのパラメーター リストに一致する引数を提供する特定のケースを処理するプロシージャのコードを記述します。</span><span class="sxs-lookup"><span data-stu-id="a697c-111">Following each declaration statement, write procedure code to handle the specific case where the calling code supplies arguments matching that version's parameter list.</span></span> <span data-ttu-id="a697c-112">必要はありませんをテストするパラメーターの呼び出し元のコードが指定されています。</span><span class="sxs-lookup"><span data-stu-id="a697c-112">You do not have to test for which parameters the calling code has supplied.</span></span> [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="a697c-113">プロシージャの対応するバージョンに制御を渡す。</span><span class="sxs-lookup"><span data-stu-id="a697c-113"> passes control to the matching version of your procedure.</span></span>  
  
4.  <span data-ttu-id="a697c-114">プロシージャの各バージョン、`End Sub`または`End Function`に応じてステートメントです。</span><span class="sxs-lookup"><span data-stu-id="a697c-114">Terminate each version of the procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a697c-115">例</span><span class="sxs-lookup"><span data-stu-id="a697c-115">Example</span></span>  
 <span data-ttu-id="a697c-116">次の例、`Sub`顧客の残高に対してトランザクションをポストするプロシージャです。</span><span class="sxs-lookup"><span data-stu-id="a697c-116">The following example defines a `Sub` procedure to post a transaction against a customer's balance.</span></span> <span data-ttu-id="a697c-117">使用して、`Overloads`して名前とその他のアカウント番号によって、顧客が使用できるプロシージャの&2; つのバージョンを定義するキーワードです。</span><span class="sxs-lookup"><span data-stu-id="a697c-117">It uses the `Overloads` keyword to define two versions of the procedure, one that accepts the customer by name and the other by account number.</span></span>  
  
 <span data-ttu-id="a697c-118">[!code-vb[VbVbcnProcedures #&72;](./codesnippet/VisualBasic/how-to-define-multiple-versions-of-a-procedure_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="a697c-118">[!code-vb[VbVbcnProcedures#72](./codesnippet/VisualBasic/how-to-define-multiple-versions-of-a-procedure_1.vb)]</span></span>  
  
 <span data-ttu-id="a697c-119">呼び出し元のコードは、いずれか、顧客 id を取得できます、`String`または`Integer`、どちらの場合も同じステートメントの呼び出しを使用します。</span><span class="sxs-lookup"><span data-stu-id="a697c-119">The calling code can obtain the customer identification as either a `String` or an `Integer`, and then use the same calling statement in either case.</span></span>  
  
 <span data-ttu-id="a697c-120">これらのバージョンを呼び出す方法の詳細について、`post`の手順を参照してください[する方法: オーバー ロードされたプロシージャを呼び出す](./how-to-call-an-overloaded-procedure.md)します。</span><span class="sxs-lookup"><span data-stu-id="a697c-120">For information on how to call these versions of the `post` procedure, see [How to: Call an Overloaded Procedure](./how-to-call-an-overloaded-procedure.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a697c-121">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="a697c-121">Compiling the Code</span></span>  
 <span data-ttu-id="a697c-122">プロシージャ名が同じで、異なるパラメーター リストを持つ、オーバー ロードされたバージョンを確認します。</span><span class="sxs-lookup"><span data-stu-id="a697c-122">Make sure each of your overloaded versions has the same procedure name but a different parameter list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a697c-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="a697c-123">See Also</span></span>  
 <span data-ttu-id="a697c-124">[手順](./index.md) </span><span class="sxs-lookup"><span data-stu-id="a697c-124">[Procedures](./index.md) </span></span>  
<span data-ttu-id="a697c-125"> [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="a697c-125"> [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="a697c-126"> [トラブルシューティングの手順](./troubleshooting-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="a697c-126"> [Troubleshooting Procedures](./troubleshooting-procedures.md) </span></span>  
<span data-ttu-id="a697c-127"> [方法: 省略可能なパラメーターを受け取るプロシージャをオーバー ロード](./how-to-overload-a-procedure-that-takes-optional-parameters.md) </span><span class="sxs-lookup"><span data-stu-id="a697c-127"> [How to: Overload a Procedure that Takes Optional Parameters](./how-to-overload-a-procedure-that-takes-optional-parameters.md) </span></span>  
<span data-ttu-id="a697c-128"> [方法: 不特定数のパラメーターを受け取るプロシージャをオーバー ロード](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md) </span><span class="sxs-lookup"><span data-stu-id="a697c-128"> [How to: Overload a Procedure that Takes an Indefinite Number of Parameters](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md) </span></span>  
<span data-ttu-id="a697c-129"> [プロシージャのオーバー ロードに関する考慮事項](./considerations-in-overloading-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="a697c-129"> [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md) </span></span>  
<span data-ttu-id="a697c-130"> [オーバーロードの解決](./overload-resolution.md)</span><span class="sxs-lookup"><span data-stu-id="a697c-130"> [Overload Resolution](./overload-resolution.md)</span></span>

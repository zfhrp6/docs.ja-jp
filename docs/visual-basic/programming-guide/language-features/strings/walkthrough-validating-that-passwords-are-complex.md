---
title: "パスワードの複雑さ (Visual Basic) の検証 |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- String data type, validation
ms.assetid: 5d9a918f-6c1f-41a3-a019-b5c2b8ce0381
caps.latest.revision: 17
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
ms.openlocfilehash: 8d636c1e43de6a108cdc217cb21aaf7689e175f7
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="walkthrough-validating-that-passwords-are-complex-visual-basic"></a><span data-ttu-id="47a2a-102">チュートリアル: パスワードの複雑さの検証 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="47a2a-102">Walkthrough: Validating That Passwords Are Complex (Visual Basic)</span></span>
<span data-ttu-id="47a2a-103">このメソッドは、いくつかの強力なパスワードの特性をチェックし、失敗したパスワードをチェックに関する情報を文字列パラメーターを更新します。</span><span class="sxs-lookup"><span data-stu-id="47a2a-103">This method checks for some strong-password characteristics and updates a string parameter with information about which checks the password fails.</span></span>  
  
 <span data-ttu-id="47a2a-104">パスワードは、ユーザーを承認するセキュリティで保護されたシステムで使用できます。</span><span class="sxs-lookup"><span data-stu-id="47a2a-104">Passwords can be used in a secure system to authorize a user.</span></span> <span data-ttu-id="47a2a-105">ただし、パスワードは、承認されていないユーザーを推測することが困難である必要があります。</span><span class="sxs-lookup"><span data-stu-id="47a2a-105">However, the passwords must be difficult for unauthorized users to guess.</span></span> <span data-ttu-id="47a2a-106">攻撃者は、使用、*辞書攻撃*プログラムでは、辞書 (または別の言語で複数の辞書) 内の単語のすべてを反復処理し、ユーザーのパスワードとして作業、単語のいずれかどうかをテストします。</span><span class="sxs-lookup"><span data-stu-id="47a2a-106">Attackers can use a *dictionary attack* program, which iterates through all of the words in a dictionary (or multiple dictionaries in different languages) and tests whether any of the words work as a user's password.</span></span> <span data-ttu-id="47a2a-107">「ヤンキース」や「ムスタング」などの脆弱なパスワードを簡単に推測できることができます。</span><span class="sxs-lookup"><span data-stu-id="47a2a-107">Weak passwords such as "Yankees" or "Mustang" can be guessed quickly.</span></span> <span data-ttu-id="47a2a-108">強力なパスワードなど、"でしょうか。'L1N3vaFiNdMeyeP@sSWerd!"に推測できる可能性が大幅に低下します。</span><span class="sxs-lookup"><span data-stu-id="47a2a-108">Stronger passwords, such as "?You'L1N3vaFiNdMeyeP@sSWerd!", are much less likely to be guessed.</span></span> <span data-ttu-id="47a2a-109">パスワードで保護されたシステムでは、強力なパスワードを選択することを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="47a2a-109">A password-protected system should ensure that users choose strong passwords.</span></span>  
  
 <span data-ttu-id="47a2a-110">強力なパスワードは、(大文字、小文字、数字、および特殊文字の組み合わせを含む) 複合語ではないです。</span><span class="sxs-lookup"><span data-stu-id="47a2a-110">A strong password is complex (containing a mixture of uppercase, lowercase, numeric, and special characters) and is not a word.</span></span> <span data-ttu-id="47a2a-111">この例では、複雑さを検証する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="47a2a-111">This example demonstrates how to verify complexity.</span></span>  
  
## <a name="example"></a><span data-ttu-id="47a2a-112">例</span><span class="sxs-lookup"><span data-stu-id="47a2a-112">Example</span></span>  
  
### <a name="code"></a><span data-ttu-id="47a2a-113">コード</span><span class="sxs-lookup"><span data-stu-id="47a2a-113">Code</span></span>  
 <span data-ttu-id="47a2a-114">[!code-vb[VbVbcnRegEx&#1;](../../../../visual-basic/programming-guide/language-features/strings/codesnippet/VisualBasic/walkthrough-validating-that-passwords-are-complex_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="47a2a-114">[!code-vb[VbVbcnRegEx#1](../../../../visual-basic/programming-guide/language-features/strings/codesnippet/VisualBasic/walkthrough-validating-that-passwords-are-complex_1.vb)]</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="47a2a-115">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="47a2a-115">Compiling the Code</span></span>  
 <span data-ttu-id="47a2a-116">このメソッドを呼び出すには、パスワードを格納する文字列を渡します。</span><span class="sxs-lookup"><span data-stu-id="47a2a-116">Call this method by passing the string that contains that password.</span></span>  
  
 <span data-ttu-id="47a2a-117">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="47a2a-117">This example requires:</span></span>  
  
-   <span data-ttu-id="47a2a-118">メンバーへのアクセス、<xref:System.Text.RegularExpressions>名前空間</xref:System.Text.RegularExpressions>。</span><span class="sxs-lookup"><span data-stu-id="47a2a-118">Access to the members of the <xref:System.Text.RegularExpressions> namespace.</span></span> <span data-ttu-id="47a2a-119">追加、`Imports`ステートメント、コード内のメンバー名を完全に修飾していない場合。</span><span class="sxs-lookup"><span data-stu-id="47a2a-119">Add an `Imports` statement if you are not fully qualifying member names in your code.</span></span> <span data-ttu-id="47a2a-120">詳細については、「[Imports ステートメント (.NET 名前空間および型)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="47a2a-120">For more information, see [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
## <a name="security"></a><span data-ttu-id="47a2a-121">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="47a2a-121">Security</span></span>  
 <span data-ttu-id="47a2a-122">ネットワーク経由でパスワードを移動する場合は、データを転送するため、安全な方法を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="47a2a-122">If you are moving the password across a network, you need to use a secure method for transferring data.</span></span> <span data-ttu-id="47a2a-123">詳細については、次を参照してください。 [ASP.NET Web アプリケーション セキュリティ](https://msdn.microsoft.com/library/330a99hc)します。</span><span class="sxs-lookup"><span data-stu-id="47a2a-123">For more information, see [ASP.NET Web Application Security](https://msdn.microsoft.com/library/330a99hc).</span></span>  
  
 <span data-ttu-id="47a2a-124">精度を向上させることができます、`ValidatePassword`の他の複雑性チェックを追加することによって機能します。</span><span class="sxs-lookup"><span data-stu-id="47a2a-124">You can improve the accuracy of the `ValidatePassword` function by adding additional complexity checks:</span></span>  
  
-   <span data-ttu-id="47a2a-125">パスワードとユーザーの名前、ユーザー id、およびアプリケーション定義の辞書からその部分文字列を比較します。</span><span class="sxs-lookup"><span data-stu-id="47a2a-125">Compare the password and its substrings against the user's name, user identifier, and an application-defined dictionary.</span></span> <span data-ttu-id="47a2a-126">さらに、比較を実行するときに、同等であるという視覚的に類似する文字を扱います。</span><span class="sxs-lookup"><span data-stu-id="47a2a-126">In addition, treat visually similar characters as equivalent when performing the comparisons.</span></span> <span data-ttu-id="47a2a-127">たとえば、「1」と「3」の数字と同等として文字"l"と"e"を扱います。</span><span class="sxs-lookup"><span data-stu-id="47a2a-127">For example, treat the letters "l" and "e" as equivalent to the numerals "1" and "3".</span></span>  
  
-   <span data-ttu-id="47a2a-128">大文字の&1; つだけの場合、パスワードの最初の文字ではないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="47a2a-128">If there is only one uppercase character, make sure it is not the password's first character.</span></span>  
  
-   <span data-ttu-id="47a2a-129">パスワードの最後の&2; つの文字がアルファベットの文字であることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="47a2a-129">Make sure that the last two characters of the password are letter characters.</span></span>  
  
-   <span data-ttu-id="47a2a-130">キーボードの一番上の行からのすべてのシンボルが入力したパスワードは許可されません。</span><span class="sxs-lookup"><span data-stu-id="47a2a-130">Do not allow passwords in which all the symbols are entered from the keyboard's top row.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47a2a-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="47a2a-131">See Also</span></span>  
 <span data-ttu-id="47a2a-132"><xref:System.Text.RegularExpressions.Regex></xref:System.Text.RegularExpressions.Regex></span><span class="sxs-lookup"><span data-stu-id="47a2a-132"><xref:System.Text.RegularExpressions.Regex></span></span>   
<span data-ttu-id="47a2a-133"> [ASP.NET Web アプリケーションのセキュリティ](https://msdn.microsoft.com/library/330a99hc)</span><span class="sxs-lookup"><span data-stu-id="47a2a-133"> [ASP.NET Web Application Security](https://msdn.microsoft.com/library/330a99hc)</span></span>

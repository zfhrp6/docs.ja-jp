---
title: パスワードの複雑さ (Visual Basic) を検証します。
ms.date: 07/20/2015
helpviewer_keywords:
- String data type [Visual Basic], validation
ms.assetid: 5d9a918f-6c1f-41a3-a019-b5c2b8ce0381
ms.openlocfilehash: acfc8ab958c8671ed7f1afd245d24a43ca12be29
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-validating-that-passwords-are-complex-visual-basic"></a><span data-ttu-id="14653-102">チュートリアル: パスワードの複雑さの検証 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="14653-102">Walkthrough: Validating That Passwords Are Complex (Visual Basic)</span></span>
<span data-ttu-id="14653-103">このメソッドは、強力なパスワードのいくつかの特性を確認しが失敗したパスワードをチェックに関する情報を含む文字列パラメーターを更新します。</span><span class="sxs-lookup"><span data-stu-id="14653-103">This method checks for some strong-password characteristics and updates a string parameter with information about which checks the password fails.</span></span>  
  
 <span data-ttu-id="14653-104">パスワードは、ユーザーを承認するセキュリティで保護されたシステムで使用できます。</span><span class="sxs-lookup"><span data-stu-id="14653-104">Passwords can be used in a secure system to authorize a user.</span></span> <span data-ttu-id="14653-105">ただし、パスワードは、承認されていないが困難になると推測する必要があります。</span><span class="sxs-lookup"><span data-stu-id="14653-105">However, the passwords must be difficult for unauthorized users to guess.</span></span> <span data-ttu-id="14653-106">攻撃者が使用できる、*辞書攻撃*プログラムでは、すべてのディクショナリ (または別の言語で複数の辞書) に単語を反復処理し、単語のすべてのユーザーのパスワードとして作業するかどうかをテストします。</span><span class="sxs-lookup"><span data-stu-id="14653-106">Attackers can use a *dictionary attack* program, which iterates through all of the words in a dictionary (or multiple dictionaries in different languages) and tests whether any of the words work as a user's password.</span></span> <span data-ttu-id="14653-107">「ヤンキース」または「ムスタング」などの脆弱なパスワードを簡単に推測できることができます。</span><span class="sxs-lookup"><span data-stu-id="14653-107">Weak passwords such as "Yankees" or "Mustang" can be guessed quickly.</span></span> <span data-ttu-id="14653-108">強力なパスワードは、たとえば"しますか?'L1N3vaFiNdMeyeP@sSWerd!"に推測できる可能性が大幅に低下します。</span><span class="sxs-lookup"><span data-stu-id="14653-108">Stronger passwords, such as "?You'L1N3vaFiNdMeyeP@sSWerd!", are much less likely to be guessed.</span></span> <span data-ttu-id="14653-109">パスワードで保護されたシステムには、強力なパスワードを選択することを確認します。</span><span class="sxs-lookup"><span data-stu-id="14653-109">A password-protected system should ensure that users choose strong passwords.</span></span>  
  
 <span data-ttu-id="14653-110">強力なパスワードは (大文字、小文字、数字、および特殊文字の組み合わせを含む) が複雑であり、word ではありません。</span><span class="sxs-lookup"><span data-stu-id="14653-110">A strong password is complex (containing a mixture of uppercase, lowercase, numeric, and special characters) and is not a word.</span></span> <span data-ttu-id="14653-111">この例では、複雑さを検証する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="14653-111">This example demonstrates how to verify complexity.</span></span>  
  
## <a name="example"></a><span data-ttu-id="14653-112">例</span><span class="sxs-lookup"><span data-stu-id="14653-112">Example</span></span>  
  
### <a name="code"></a><span data-ttu-id="14653-113">コード</span><span class="sxs-lookup"><span data-stu-id="14653-113">Code</span></span>  
 [!code-vb[VbVbcnRegEx#1](../../../../visual-basic/programming-guide/language-features/strings/codesnippet/VisualBasic/walkthrough-validating-that-passwords-are-complex_1.vb)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="14653-114">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="14653-114">Compiling the Code</span></span>  
 <span data-ttu-id="14653-115">パスワードを格納する文字列を渡すことによって、このメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="14653-115">Call this method by passing the string that contains that password.</span></span>  
  
 <span data-ttu-id="14653-116">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="14653-116">This example requires:</span></span>  
  
-   <span data-ttu-id="14653-117"><xref:System.Text.RegularExpressions> 名前空間のメンバーへのアクセス許可。</span><span class="sxs-lookup"><span data-stu-id="14653-117">Access to the members of the <xref:System.Text.RegularExpressions> namespace.</span></span> <span data-ttu-id="14653-118">コード内でメンバー名を完全修飾していない場合は、`Imports` ステートメントを追加します。</span><span class="sxs-lookup"><span data-stu-id="14653-118">Add an `Imports` statement if you are not fully qualifying member names in your code.</span></span> <span data-ttu-id="14653-119">詳細については、「[Imports ステートメント (.NET 名前空間および型)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="14653-119">For more information, see [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
## <a name="security"></a><span data-ttu-id="14653-120">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="14653-120">Security</span></span>  
 <span data-ttu-id="14653-121">パスワードをネットワーク経由で移動する場合は、データを転送するため、セキュリティで保護されたメソッドを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="14653-121">If you are moving the password across a network, you need to use a secure method for transferring data.</span></span> <span data-ttu-id="14653-122">詳細については、次を参照してください。 [ASP.NET Web アプリケーションのセキュリティ](https://msdn.microsoft.com/library/330a99hc)です。</span><span class="sxs-lookup"><span data-stu-id="14653-122">For more information, see [ASP.NET Web Application Security](https://msdn.microsoft.com/library/330a99hc).</span></span>  
  
 <span data-ttu-id="14653-123">精度を向上させることができます、`ValidatePassword`の他の複雑性チェックを追加することによって機能します。</span><span class="sxs-lookup"><span data-stu-id="14653-123">You can improve the accuracy of the `ValidatePassword` function by adding additional complexity checks:</span></span>  
  
-   <span data-ttu-id="14653-124">パスワードとユーザーの名前、ユーザー識別子、およびアプリケーション定義の辞書に対してその部分文字列を比較します。</span><span class="sxs-lookup"><span data-stu-id="14653-124">Compare the password and its substrings against the user's name, user identifier, and an application-defined dictionary.</span></span> <span data-ttu-id="14653-125">さらに、比較を実行するときに、同等と視覚的に類似する文字を処理します。</span><span class="sxs-lookup"><span data-stu-id="14653-125">In addition, treat visually similar characters as equivalent when performing the comparisons.</span></span> <span data-ttu-id="14653-126">たとえば、「1」と「3」の数字と同等として文字"l"と"e"を扱います。</span><span class="sxs-lookup"><span data-stu-id="14653-126">For example, treat the letters "l" and "e" as equivalent to the numerals "1" and "3".</span></span>  
  
-   <span data-ttu-id="14653-127">1 つだけ大文字の文字がある場合、パスワードの最初の文字ではないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="14653-127">If there is only one uppercase character, make sure it is not the password's first character.</span></span>  
  
-   <span data-ttu-id="14653-128">パスワードの最後の 2 つの文字が文字であることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="14653-128">Make sure that the last two characters of the password are letter characters.</span></span>  
  
-   <span data-ttu-id="14653-129">すべてのシンボルがキーボードの一番上の行から入力したパスワードは許可されません。</span><span class="sxs-lookup"><span data-stu-id="14653-129">Do not allow passwords in which all the symbols are entered from the keyboard's top row.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14653-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="14653-130">See Also</span></span>  
 <xref:System.Text.RegularExpressions.Regex>  
 [<span data-ttu-id="14653-131">ASP.NET Web アプリケーションのセキュリティ</span><span class="sxs-lookup"><span data-stu-id="14653-131">ASP.NET Web Application Security</span></span>](https://msdn.microsoft.com/library/330a99hc)

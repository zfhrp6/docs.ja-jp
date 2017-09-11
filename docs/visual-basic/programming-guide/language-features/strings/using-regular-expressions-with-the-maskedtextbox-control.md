---
title: "Visual Basic の MaskedTextBox コントロールによる正規表現の使用 |Microsoft ドキュメント"
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
- strings [Visual Basic], regular expressions
- strings [Visual Basic], masked edit
ms.assetid: 2a048fb0-7053-487d-b2c5-ffa5e22ed6f9
caps.latest.revision: 10
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
ms.openlocfilehash: 66f61eed8bc8431392d7216ffb799b221489f332
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="using-regular-expressions-with-the-maskedtextbox-control-in-visual-basic"></a><span data-ttu-id="06cb2-102">Visual Basic の MaskedTextBox コントロールによる正規表現を使用する</span><span class="sxs-lookup"><span data-stu-id="06cb2-102">Using Regular Expressions with the MaskedTextBox Control in Visual Basic</span></span>
<span data-ttu-id="06cb2-103">この例を使用する単純な正規表現に変換する方法、<xref:System.Windows.Forms.MaskedTextBox>コントロール</xref:System.Windows.Forms.MaskedTextBox>。</span><span class="sxs-lookup"><span data-stu-id="06cb2-103">This example demonstrates how to convert simple regular expressions to work with the <xref:System.Windows.Forms.MaskedTextBox> control.</span></span>  
  
## <a name="description-of-the-masking-language"></a><span data-ttu-id="06cb2-104">マスク言語の説明</span><span class="sxs-lookup"><span data-stu-id="06cb2-104">Description of the Masking Language</span></span>  
 <span data-ttu-id="06cb2-105">標準的な<xref:System.Windows.Forms.MaskedTextBox>マスク言語で使用される 1 つに基づいて、`Masked Edit`で制御[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]6.0 し、そのプラットフォームから移行するユーザーにとって理解する必要があります</xref:System.Windows.Forms.MaskedTextBox>。</span><span class="sxs-lookup"><span data-stu-id="06cb2-105">The standard <xref:System.Windows.Forms.MaskedTextBox> masking language is based on the one used by the `Masked Edit` control in [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 6.0 and should be familiar to users migrating from that platform.</span></span>  
  
 <span data-ttu-id="06cb2-106"><xref:System.Windows.Forms.MaskedTextBox.Mask%2A>のプロパティ、<xref:System.Windows.Forms.MaskedTextBox>コントロールを使用するどのような入力マスクを指定します</xref:System.Windows.Forms.MaskedTextBox></xref:System.Windows.Forms.MaskedTextBox.Mask%2A>。</span><span class="sxs-lookup"><span data-stu-id="06cb2-106">The <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> property of the <xref:System.Windows.Forms.MaskedTextBox> control specifies what input mask to use.</span></span> <span data-ttu-id="06cb2-107">マスクは、1 つ以上の次の表からマスク要素から成る文字列である必要があります。</span><span class="sxs-lookup"><span data-stu-id="06cb2-107">The mask must be a string composed of one or more of the masking elements from the following table.</span></span>  
  
|<span data-ttu-id="06cb2-108">マスク要素</span><span class="sxs-lookup"><span data-stu-id="06cb2-108">Masking element</span></span>|<span data-ttu-id="06cb2-109">説明</span><span class="sxs-lookup"><span data-stu-id="06cb2-109">Description</span></span>|<span data-ttu-id="06cb2-110">正規表現の要素</span><span class="sxs-lookup"><span data-stu-id="06cb2-110">Regular expression element</span></span>|  
|---------------------|-----------------|--------------------------------|  
|<span data-ttu-id="06cb2-111">0</span><span class="sxs-lookup"><span data-stu-id="06cb2-111">0</span></span>|<span data-ttu-id="06cb2-112">0 ~ 9 で任意の単一数字です。</span><span class="sxs-lookup"><span data-stu-id="06cb2-112">Any single digit between 0 and 9.</span></span> <span data-ttu-id="06cb2-113">入力することができます。</span><span class="sxs-lookup"><span data-stu-id="06cb2-113">Entry required.</span></span>|<span data-ttu-id="06cb2-114">\d</span><span class="sxs-lookup"><span data-stu-id="06cb2-114">\d</span></span>|  
|<span data-ttu-id="06cb2-115">9</span><span class="sxs-lookup"><span data-stu-id="06cb2-115">9</span></span>|<span data-ttu-id="06cb2-116">数字または空白。</span><span class="sxs-lookup"><span data-stu-id="06cb2-116">Digit or space.</span></span> <span data-ttu-id="06cb2-117">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="06cb2-117">Entry optional.</span></span>|<span data-ttu-id="06cb2-118">[ \d]?</span><span class="sxs-lookup"><span data-stu-id="06cb2-118">[ \d]?</span></span>|  
|#|<span data-ttu-id="06cb2-119">数字または空白。</span><span class="sxs-lookup"><span data-stu-id="06cb2-119">Digit or space.</span></span> <span data-ttu-id="06cb2-120">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="06cb2-120">Entry optional.</span></span> <span data-ttu-id="06cb2-121">この位置は、マスクの空白のまま、それはスペースとしてレンダリングされます。</span><span class="sxs-lookup"><span data-stu-id="06cb2-121">If this position is left blank in the mask, it will be rendered as a space.</span></span> <span data-ttu-id="06cb2-122">プラス記号 (+)、マイナス記号 (-) 記号を許可します。</span><span class="sxs-lookup"><span data-stu-id="06cb2-122">Plus (+) and minus (-) signs are allowed.</span></span>|<span data-ttu-id="06cb2-123">[ \d+-]?</span><span class="sxs-lookup"><span data-stu-id="06cb2-123">[ \d+-]?</span></span>|  
|<span data-ttu-id="06cb2-124">L</span><span class="sxs-lookup"><span data-stu-id="06cb2-124">L</span></span>|<span data-ttu-id="06cb2-125">ASCII 文字。</span><span class="sxs-lookup"><span data-stu-id="06cb2-125">ASCII letter.</span></span> <span data-ttu-id="06cb2-126">入力することができます。</span><span class="sxs-lookup"><span data-stu-id="06cb2-126">Entry required.</span></span>|<span data-ttu-id="06cb2-127">[- A-za-z]</span><span class="sxs-lookup"><span data-stu-id="06cb2-127">[a-zA-Z]</span></span>|  
|<span data-ttu-id="06cb2-128">?</span><span class="sxs-lookup"><span data-stu-id="06cb2-128">?</span></span>|<span data-ttu-id="06cb2-129">ASCII 文字。</span><span class="sxs-lookup"><span data-stu-id="06cb2-129">ASCII letter.</span></span> <span data-ttu-id="06cb2-130">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="06cb2-130">Entry optional.</span></span>|<span data-ttu-id="06cb2-131">[- A-za-z] でしょうか。</span><span class="sxs-lookup"><span data-stu-id="06cb2-131">[a-zA-Z]?</span></span>|  
|&|<span data-ttu-id="06cb2-132">文字です。</span><span class="sxs-lookup"><span data-stu-id="06cb2-132">Character.</span></span> <span data-ttu-id="06cb2-133">入力することができます。</span><span class="sxs-lookup"><span data-stu-id="06cb2-133">Entry required.</span></span>|<span data-ttu-id="06cb2-134">[\p{Ll}\p{Lu}\p{Lt}\p{Lm}\p{Lo}]</span><span class="sxs-lookup"><span data-stu-id="06cb2-134">[\p{Ll}\p{Lu}\p{Lt}\p{Lm}\p{Lo}]</span></span>|  
|<span data-ttu-id="06cb2-135">C</span><span class="sxs-lookup"><span data-stu-id="06cb2-135">C</span></span>|<span data-ttu-id="06cb2-136">文字です。</span><span class="sxs-lookup"><span data-stu-id="06cb2-136">Character.</span></span> <span data-ttu-id="06cb2-137">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="06cb2-137">Entry optional.</span></span>|<span data-ttu-id="06cb2-138">[\p{Ll}\p{Lu}\p{Lt}\p{Lm}\p{Lo}] ですか。</span><span class="sxs-lookup"><span data-stu-id="06cb2-138">[\p{Ll}\p{Lu}\p{Lt}\p{Lm}\p{Lo}]?</span></span>|  
|<span data-ttu-id="06cb2-139">A</span><span class="sxs-lookup"><span data-stu-id="06cb2-139">A</span></span>|<span data-ttu-id="06cb2-140">英数字。</span><span class="sxs-lookup"><span data-stu-id="06cb2-140">Alphanumeric.</span></span> <span data-ttu-id="06cb2-141">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="06cb2-141">Entry optional.</span></span>|<span data-ttu-id="06cb2-142">\W</span><span class="sxs-lookup"><span data-stu-id="06cb2-142">\W</span></span>|  
|<span data-ttu-id="06cb2-143">」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="06cb2-143">.</span></span>|<span data-ttu-id="06cb2-144">カルチャに応じた小数点のプレース ホルダーです。</span><span class="sxs-lookup"><span data-stu-id="06cb2-144">Culture-appropriate decimal placeholder.</span></span>|<span data-ttu-id="06cb2-145">使用できません。</span><span class="sxs-lookup"><span data-stu-id="06cb2-145">Not available.</span></span>|  
|<span data-ttu-id="06cb2-146">、</span><span class="sxs-lookup"><span data-stu-id="06cb2-146">,</span></span>|<span data-ttu-id="06cb2-147">何千ものカルチャに応じたプレース ホルダーです。</span><span class="sxs-lookup"><span data-stu-id="06cb2-147">Culture-appropriate thousands placeholder.</span></span>|<span data-ttu-id="06cb2-148">使用できません。</span><span class="sxs-lookup"><span data-stu-id="06cb2-148">Not available.</span></span>|  
|<span data-ttu-id="06cb2-149">:</span><span class="sxs-lookup"><span data-stu-id="06cb2-149">:</span></span>|<span data-ttu-id="06cb2-150">カルチャに応じた時刻の区切り記号。</span><span class="sxs-lookup"><span data-stu-id="06cb2-150">Culture-appropriate time separator.</span></span>|<span data-ttu-id="06cb2-151">使用できません。</span><span class="sxs-lookup"><span data-stu-id="06cb2-151">Not available.</span></span>|  
|/|<span data-ttu-id="06cb2-152">カルチャに応じた日付の区切り記号。</span><span class="sxs-lookup"><span data-stu-id="06cb2-152">Culture-appropriate date separator.</span></span>|<span data-ttu-id="06cb2-153">使用できません。</span><span class="sxs-lookup"><span data-stu-id="06cb2-153">Not available.</span></span>|  
|$|<span data-ttu-id="06cb2-154">カルチャに応じた通貨記号。</span><span class="sxs-lookup"><span data-stu-id="06cb2-154">Culture-appropriate currency symbol.</span></span>|<span data-ttu-id="06cb2-155">使用できません。</span><span class="sxs-lookup"><span data-stu-id="06cb2-155">Not available.</span></span>|  
|\<|<span data-ttu-id="06cb2-156">小文字に変換後に続くすべての文字に変換します。</span><span class="sxs-lookup"><span data-stu-id="06cb2-156">Converts all characters that follow to lowercase.</span></span>|<span data-ttu-id="06cb2-157">使用できません。</span><span class="sxs-lookup"><span data-stu-id="06cb2-157">Not available.</span></span>|  
|>|<span data-ttu-id="06cb2-158">大文字に続くすべての文字に変換します。</span><span class="sxs-lookup"><span data-stu-id="06cb2-158">Converts all characters that follow to uppercase.</span></span>|<span data-ttu-id="06cb2-159">使用できません。</span><span class="sxs-lookup"><span data-stu-id="06cb2-159">Not available.</span></span>|  
|<span data-ttu-id="06cb2-160">&#124;</span><span class="sxs-lookup"><span data-stu-id="06cb2-160">&#124;</span></span>|<span data-ttu-id="06cb2-161">以前のシフトを元に戻すか、下方向にシフトします。</span><span class="sxs-lookup"><span data-stu-id="06cb2-161">Undoes a previous shift up or shift down.</span></span>|<span data-ttu-id="06cb2-162">使用できません。</span><span class="sxs-lookup"><span data-stu-id="06cb2-162">Not available.</span></span>|  
|\|<span data-ttu-id="06cb2-163">リテラルに変えるマスク文字をエスケープします。</span><span class="sxs-lookup"><span data-stu-id="06cb2-163">Escapes a mask character, turning it into a literal.</span></span> <span data-ttu-id="06cb2-164">"\\\\"円記号のエスケープ シーケンスです。</span><span class="sxs-lookup"><span data-stu-id="06cb2-164">"\\\\" is the escape sequence for a backslash.</span></span>|\|  
|<span data-ttu-id="06cb2-165">その他のすべての文字。</span><span class="sxs-lookup"><span data-stu-id="06cb2-165">All other characters.</span></span>|<span data-ttu-id="06cb2-166">リテラルです。</span><span class="sxs-lookup"><span data-stu-id="06cb2-166">Literals.</span></span> <span data-ttu-id="06cb2-167">マスク以外のすべての要素は<xref:System.Windows.Forms.MaskedTextBox>。</xref:System.Windows.Forms.MaskedTextBox>自体として表示されます。</span><span class="sxs-lookup"><span data-stu-id="06cb2-167">All non-mask elements will appear as themselves within <xref:System.Windows.Forms.MaskedTextBox>.</span></span>|<span data-ttu-id="06cb2-168">その他のすべての文字。</span><span class="sxs-lookup"><span data-stu-id="06cb2-168">All other characters.</span></span>|  
  
 <span data-ttu-id="06cb2-169">小数点 (.)、桁区切り (,)、時間 (:)、日付 (/)、および通貨 ($) 記号は、アプリケーションのカルチャで定義された記号で表示する既定です。</span><span class="sxs-lookup"><span data-stu-id="06cb2-169">The decimal (.), thousandths (,), time (:), date (/), and currency ($) symbols default to displaying those symbols as defined by the application's culture.</span></span> <span data-ttu-id="06cb2-170">別のカルチャのシンボルを使用して、表示を強制することができます、<xref:System.Windows.Forms.MaskedTextBox.FormatProvider%2A>プロパティ</xref:System.Windows.Forms.MaskedTextBox.FormatProvider%2A>。</span><span class="sxs-lookup"><span data-stu-id="06cb2-170">You can force them to display symbols for another culture by using the <xref:System.Windows.Forms.MaskedTextBox.FormatProvider%2A> property.</span></span>  
  
## <a name="regular-expressions-and-masks"></a><span data-ttu-id="06cb2-171">正規表現とマスク</span><span class="sxs-lookup"><span data-stu-id="06cb2-171">Regular Expressions and Masks</span></span>  
 <span data-ttu-id="06cb2-172">正規表現とマスクを使用するには、ユーザー入力を検証する、完全に同等ではありません。</span><span class="sxs-lookup"><span data-stu-id="06cb2-172">Although you can use regular expressions and masks to validate user input, they are not completely equivalent.</span></span> <span data-ttu-id="06cb2-173">正規表現は定型より複雑なパターンを表すことができますが、簡潔にして、カルチャに応じた形式で、マスクは、同じ情報を表すことができます。</span><span class="sxs-lookup"><span data-stu-id="06cb2-173">Regular expressions can express more complex patterns than masks, but masks can express the same information more succinctly and in a culturally relevant format.</span></span>  
  
 <span data-ttu-id="06cb2-174">次の表は、それぞれの&4; つの正規表現と等価のマスクを比較します。</span><span class="sxs-lookup"><span data-stu-id="06cb2-174">The following table compares four regular expressions and the equivalent mask for each.</span></span>  
  
|<span data-ttu-id="06cb2-175">正規表現</span><span class="sxs-lookup"><span data-stu-id="06cb2-175">Regular Expression</span></span>|<span data-ttu-id="06cb2-176">マスク</span><span class="sxs-lookup"><span data-stu-id="06cb2-176">Mask</span></span>|<span data-ttu-id="06cb2-177">ノート</span><span class="sxs-lookup"><span data-stu-id="06cb2-177">Notes</span></span>|  
|------------------------|----------|-----------|  
|`\d{2}/\d{2}/\d{4}`|`00/00/0000`|<span data-ttu-id="06cb2-178">`/`マスク内の文字は、論理上の日付の区切り記号と、アプリケーションの現在のカルチャに適切な日付の区切り記号としてユーザーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="06cb2-178">The `/` character in the mask is a logical date separator, and it will appear to the user as the date separator appropriate to the application's current culture.</span></span>|  
|`\d{2}-[A-Z][a-z]{2}-\d{4}`|`00->L<LL-0000`|<span data-ttu-id="06cb2-179">初期文字を大文字小文字の&2; つ続けて&3; 桁の月の省略形が表示される米国形式の日付 (日、月の省略名、および年)。</span><span class="sxs-lookup"><span data-stu-id="06cb2-179">A date (day, month abbreviation, and year) in United States format in which the three-letter month abbreviation is displayed with an initial uppercase letter followed by two lowercase letters.</span></span>|  
|`(\(\d{3}\)-)?\d{3}-d{4}`|`(999)-000-0000`|<span data-ttu-id="06cb2-180">アメリカ合衆国の電話番号、市外局番の省略可能です。</span><span class="sxs-lookup"><span data-stu-id="06cb2-180">United States phone number, area code optional.</span></span> <span data-ttu-id="06cb2-181">ユーザーは省略可能な文字を入力しない場合は、彼女は入力するスペースか最初の 0 で表されるマスク内の位置に直接マウス ポインターを置きます。</span><span class="sxs-lookup"><span data-stu-id="06cb2-181">If the user does not wish to enter the optional characters, she can either enter spaces or place the mouse pointer directly at the position in the mask represented by the first 0.</span></span>|  
|`$\d{6}.00`|`$999,999.00`|<span data-ttu-id="06cb2-182">0 ~ 999999 の範囲の通貨値。</span><span class="sxs-lookup"><span data-stu-id="06cb2-182">A currency value in the range of 0 to 999999.</span></span> <span data-ttu-id="06cb2-183">通貨、区切り記号、および&10; 進数の文字は置き換えられます実行時に、対応するカルチャに固有です。</span><span class="sxs-lookup"><span data-stu-id="06cb2-183">The currency, thousandth, and decimal characters will be replaced at run-time with their culture-specific equivalents.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="06cb2-184">関連項目</span><span class="sxs-lookup"><span data-stu-id="06cb2-184">See Also</span></span>  
 <span data-ttu-id="06cb2-185"><xref:System.Windows.Forms.MaskedTextBox.Mask%2A></xref:System.Windows.Forms.MaskedTextBox.Mask%2A></span><span class="sxs-lookup"><span data-stu-id="06cb2-185"><xref:System.Windows.Forms.MaskedTextBox.Mask%2A></span></span>   
 <span data-ttu-id="06cb2-186"><xref:System.Windows.Forms.MaskedTextBox></xref:System.Windows.Forms.MaskedTextBox></span><span class="sxs-lookup"><span data-stu-id="06cb2-186"><xref:System.Windows.Forms.MaskedTextBox></span></span>   
<span data-ttu-id="06cb2-187"> [Visual Basic における文字列の検証](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md) </span><span class="sxs-lookup"><span data-stu-id="06cb2-187"> [Validating Strings in Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md) </span></span>  
<span data-ttu-id="06cb2-188"> [MaskedTextBox コントロール](http://msdn.microsoft.com/library/235d6121-027d-481d-8d59-4f6794d15d0c)</span><span class="sxs-lookup"><span data-stu-id="06cb2-188"> [MaskedTextBox Control](http://msdn.microsoft.com/library/235d6121-027d-481d-8d59-4f6794d15d0c)</span></span>

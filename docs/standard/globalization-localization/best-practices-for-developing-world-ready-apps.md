---
title: "推奨される国際対応アプリケーション開発手順"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- global applications, best practices
- world-ready applications, best practices
- globalization [.NET Framework], best practices
- international applications [.NET Framework], best practices
ms.assetid: f08169c7-aad8-4ec3-9a21-9ebd3b89986c
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 1fbdbe2596f44a6efda35b8c3e3aace303d79364
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="best-practices-for-developing-world-ready-applications"></a><span data-ttu-id="6b6d0-102">推奨される国際対応アプリケーション開発手順</span><span class="sxs-lookup"><span data-stu-id="6b6d0-102">Best Practices for Developing World-Ready Applications</span></span>
<span data-ttu-id="6b6d0-103">このセクションでは、推奨される国際対応アプリケーション開発手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="6b6d0-103">This section describes the best practices to follow when developing world-ready applications.</span></span>  
  
## <a name="globalization-best-practices"></a><span data-ttu-id="6b6d0-104">推奨されるグローバリゼーション手順</span><span class="sxs-lookup"><span data-stu-id="6b6d0-104">Globalization Best Practices</span></span>  
  
1.  <span data-ttu-id="6b6d0-105">アプリケーションを内部的に Unicode アプリケーションにします。</span><span class="sxs-lookup"><span data-stu-id="6b6d0-105">Make your application Unicode internally.</span></span>  
  
2.  <span data-ttu-id="6b6d0-106">データの操作と書式指定には、<xref:System.Globalization> 名前空間のカルチャ認識クラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="6b6d0-106">Use the culture-aware classes provided by the <xref:System.Globalization> namespace to manipulate and format data.</span></span>  
  
    -   <span data-ttu-id="6b6d0-107">並べ替えには <xref:System.Globalization.SortKey> クラスと <xref:System.Globalization.CompareInfo> クラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="6b6d0-107">For sorting, use the <xref:System.Globalization.SortKey> class and the <xref:System.Globalization.CompareInfo> class.</span></span>  
  
    -   <span data-ttu-id="6b6d0-108">文字列比較には、<xref:System.Globalization.CompareInfo> クラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="6b6d0-108">For string comparisons, use the <xref:System.Globalization.CompareInfo> class.</span></span>  
  
    -   <span data-ttu-id="6b6d0-109">日付と時刻の書式指定には、<xref:System.Globalization.DateTimeFormatInfo> クラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="6b6d0-109">For date and time formatting, use the <xref:System.Globalization.DateTimeFormatInfo> class.</span></span>  
  
    -   <span data-ttu-id="6b6d0-110">数値書式指定には、<xref:System.Globalization.NumberFormatInfo> クラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="6b6d0-110">For numeric formatting, use the <xref:System.Globalization.NumberFormatInfo> class.</span></span>  
  
    -   <span data-ttu-id="6b6d0-111">グレゴリオ暦とグレゴリオ暦以外の暦には、<xref:System.Globalization.Calendar> クラスまたは特定のカレンダー実装を使用します。</span><span class="sxs-lookup"><span data-stu-id="6b6d0-111">For Gregorian and non-Gregorian calendars, use the <xref:System.Globalization.Calendar> class or one of the specific calendar implementations.</span></span>  
  
3.  <span data-ttu-id="6b6d0-112">状況に応じて、<xref:System.Globalization.CultureInfo?displayProperty=nameWithType> クラスのカルチャ プロパティ設定を使用します。</span><span class="sxs-lookup"><span data-stu-id="6b6d0-112">Use the culture property settings provided by the <xref:System.Globalization.CultureInfo?displayProperty=nameWithType> class in the appropriate situations.</span></span> <span data-ttu-id="6b6d0-113">日付と時刻や数値の書式指定などの書式指定処理には、<xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="6b6d0-113">Use the <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> property for formatting tasks, such as date and time or numeric formatting.</span></span> <span data-ttu-id="6b6d0-114">リソースを取得するには、<xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="6b6d0-114">Use the <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> property to retrieve resources.</span></span> <span data-ttu-id="6b6d0-115">`CurrentCulture` プロパティと `CurrentUICulture` プロパティはスレッドごとに設定できることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="6b6d0-115">Note that the `CurrentCulture` and `CurrentUICulture` properties can be set per thread.</span></span>  
  
4.  <span data-ttu-id="6b6d0-116"><xref:System.Text> 名前空間のエンコーディング クラスを使用して、アプリケーションでの各種エンコーディングのデータの読み取り操作と書き込み操作を有効にします。</span><span class="sxs-lookup"><span data-stu-id="6b6d0-116">Enable your application to read and write data to and from a variety of encodings by using the encoding classes in the <xref:System.Text> namespace.</span></span> <span data-ttu-id="6b6d0-117">常に ASCII データが使用されるとは限らないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="6b6d0-117">Do not assume ASCII data.</span></span> <span data-ttu-id="6b6d0-118">どのようなテキスト入力でも、各種の言語の文字が使用される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="6b6d0-118">Assume that international characters will be supplied anywhere a user can enter text.</span></span> <span data-ttu-id="6b6d0-119">たとえば、アプリケーションは、サーバー名、ディレクトリ名、ファイル名、ユーザー名、および URL に含まれる各種言語の文字を受け入れる必要があります。</span><span class="sxs-lookup"><span data-stu-id="6b6d0-119">For example, the application should accept international characters in server names, directories, file names, user names, and URLs.</span></span>  
  
5.  <span data-ttu-id="6b6d0-120"><xref:System.Text.UTF8Encoding> クラスを使用する場合は、セキュリティ上の理由から、このクラスに用意されているエラー検出機能を使用してください。</span><span class="sxs-lookup"><span data-stu-id="6b6d0-120">When using the <xref:System.Text.UTF8Encoding> class, for security reasons, use the error detection feature offered by this class.</span></span> <span data-ttu-id="6b6d0-121">エラー検出機能を有効にするには、`throwOnInvalidBytes` パラメーターを受け取るコンストラクターを使用してクラスのインスタンスを作成し、このパラメーターの値を `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="6b6d0-121">To turn on the error detection feature, the application creates an instance of the class using the constructor that takes a `throwOnInvalidBytes` parameter and sets the value of this parameter to `true`.</span></span>  
  
6.  <span data-ttu-id="6b6d0-122">文字列は、できるだけ全体を 1 つのまとまりとして扱い、個々の文字の連続として処理しないようにします。</span><span class="sxs-lookup"><span data-stu-id="6b6d0-122">Whenever possible, handle strings as entire strings instead of as a series of individual characters.</span></span> <span data-ttu-id="6b6d0-123">これは特に部分文字列の並べ替えと検索で重要です。</span><span class="sxs-lookup"><span data-stu-id="6b6d0-123">This is especially important when sorting or searching for substrings.</span></span> <span data-ttu-id="6b6d0-124">これにより、組み合わせ文字の解析に関連する問題の発生を防ぐことができます。</span><span class="sxs-lookup"><span data-stu-id="6b6d0-124">This will prevent problems associated with parsing combined characters.</span></span>  
  
7.  <span data-ttu-id="6b6d0-125"><xref:System.Drawing> 名前空間のクラスを使用してテキストを表示します。</span><span class="sxs-lookup"><span data-stu-id="6b6d0-125">Display text using the classes provided by the <xref:System.Drawing> namespace.</span></span>  
  
8.  <span data-ttu-id="6b6d0-126">オペレーティング システム間での一貫性を維持するため、ユーザー設定によって <xref:System.Globalization.CultureInfo> がオーバーライドされないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="6b6d0-126">For consistency across operating systems, do not allow user settings to override <xref:System.Globalization.CultureInfo>.</span></span> <span data-ttu-id="6b6d0-127">`CultureInfo` パラメーターを受け取る `useUserOverride` コンストラクターを使用し、このパラメーターを `false` に設定してください。</span><span class="sxs-lookup"><span data-stu-id="6b6d0-127">Use the `CultureInfo` constructor that accepts a `useUserOverride` parameter and set it to `false`.</span></span>  
  
9. <span data-ttu-id="6b6d0-128">国際対応オペレーティング システムで、国際対応データを使用してアプリケーションの機能をテストします。</span><span class="sxs-lookup"><span data-stu-id="6b6d0-128">Test your application functionality on international operating system versions, using international data.</span></span>  
  
10. <span data-ttu-id="6b6d0-129">文字列比較操作または大文字と小文字の変更操作の結果に基づいてセキュリティ上の決定を行う場合は、アプリケーションで実行する操作がカルチャに依存しないようにします。</span><span class="sxs-lookup"><span data-stu-id="6b6d0-129">If a security decision is based on the result of a string comparison or case change operation, have the application perform a culture-insensitive operation.</span></span> <span data-ttu-id="6b6d0-130">こうすることで、`CultureInfo.CurrentCulture` の値が結果に影響を及ぼすことがなくなります。</span><span class="sxs-lookup"><span data-stu-id="6b6d0-130">This practice ensures that the result is not affected by the value of `CultureInfo.CurrentCulture`.</span></span> <span data-ttu-id="6b6d0-131">カルチャに依存した文字列比較により矛盾した結果がどのように生成されるかを示す例については、「[文字列を使用するためのベスト プラクティス](../../../docs/standard/base-types/best-practices-strings.md)」の「現在のカルチャを使用する文字列比較」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="6b6d0-131">See the "String Comparisons that Use the Current Culture" section of [Best Practices for Using Strings](../../../docs/standard/base-types/best-practices-strings.md) for an example that demonstrates how culture-sensitive string comparisons can produce inconsistent results.</span></span>  
  
## <a name="localization-best-practices"></a><span data-ttu-id="6b6d0-132">推奨されるローカリゼーション手順</span><span class="sxs-lookup"><span data-stu-id="6b6d0-132">Localization Best Practices</span></span>  
  
1.  <span data-ttu-id="6b6d0-133">ローカライズ可能なすべてのリソースをリソース専用 DLL へ移動します。</span><span class="sxs-lookup"><span data-stu-id="6b6d0-133">Move all localizable resources to separate resource-only DLLs.</span></span> <span data-ttu-id="6b6d0-134">ローカライズ可能リソースには、文字列、エラー メッセージ、ダイアログ ボックス、メニュー、埋め込みオブジェクト リソースなどのユーザー インターフェイス要素があります。</span><span class="sxs-lookup"><span data-stu-id="6b6d0-134">Localizable resources include user interface elements, such as strings, error messages, dialog boxes, menus, and embedded object resources.</span></span>  
  
2.  <span data-ttu-id="6b6d0-135">文字列やユーザー インターフェイス リソースをハードコーディングしないでください。</span><span class="sxs-lookup"><span data-stu-id="6b6d0-135">Do not hardcode strings or user interface resources.</span></span>  
  
3.  <span data-ttu-id="6b6d0-136">ローカライズできないリソースをリソース専用 DLL に含めないでください。</span><span class="sxs-lookup"><span data-stu-id="6b6d0-136">Do not put nonlocalizable resources into the resource-only DLLs.</span></span> <span data-ttu-id="6b6d0-137">ローカライズを行う翻訳者を混乱させる原因となります。</span><span class="sxs-lookup"><span data-stu-id="6b6d0-137">This causes confusion for translators.</span></span>  
  
4.  <span data-ttu-id="6b6d0-138">文字列を実行時に連結して使う方法は避けてください。</span><span class="sxs-lookup"><span data-stu-id="6b6d0-138">Do not use composite strings that are built at run time from concatenated phrases.</span></span> <span data-ttu-id="6b6d0-139">連結される文字列は、英語の語順に依存することが多く、ほかの言語でのローカライズ作業が困難になります。</span><span class="sxs-lookup"><span data-stu-id="6b6d0-139">Composite strings are difficult to localize because they often assume an English grammatical order that does not apply to all languages.</span></span>  
  
5.  <span data-ttu-id="6b6d0-140">"Empty Folder" のように、構成要素の文法的な役割によって複数の翻訳が存在するあいまいな文字列を使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="6b6d0-140">Avoid ambiguous constructs such as "Empty Folder" where the strings can be translated differently depending on the grammatical roles of the string components.</span></span> <span data-ttu-id="6b6d0-141">たとえば、"empty" は動詞または形容詞として解釈できるため、イタリア語やフランス語などの言語での翻訳結果が異なることがあります。</span><span class="sxs-lookup"><span data-stu-id="6b6d0-141">For example, "empty" can be either a verb or an adjective, which can lead to different translations in languages such as Italian or French.</span></span>  
  
6.  <span data-ttu-id="6b6d0-142">アプリケーションではテキストが含まれているイメージやアイコンを使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="6b6d0-142">Avoid using images and icons that contain text in your application.</span></span> <span data-ttu-id="6b6d0-143">このようなイメージやアイコンのローカライズには時間と労力がかかります。</span><span class="sxs-lookup"><span data-stu-id="6b6d0-143">They are expensive to localize.</span></span>  
  
7.  <span data-ttu-id="6b6d0-144">ユーザー インターフェイスの文字列は、表示領域に余裕がある程度の長さにしておいてください。</span><span class="sxs-lookup"><span data-stu-id="6b6d0-144">Allow plenty of room for the length of strings to expand in the user interface.</span></span> <span data-ttu-id="6b6d0-145">言語によっては、ユーザー インターフェイスが他の言語よりも 50 ～ 75% 長い領域を必要とする場合があります。</span><span class="sxs-lookup"><span data-stu-id="6b6d0-145">In some languages, phrases can require 50-75 percent more space than they need in other languages.</span></span>  
  
8.  <span data-ttu-id="6b6d0-146">カルチャに基づいてリソースを取得するには、<xref:System.Resources.ResourceManager?displayProperty=nameWithType> クラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="6b6d0-146">Use the <xref:System.Resources.ResourceManager?displayProperty=nameWithType> class to retrieve resources based on culture.</span></span>  
  
9. <span data-ttu-id="6b6d0-147">Windows フォームのダイアログ ボックスを作成するには Visual Studio を使います。このように作成されたダイアログ ボックスは、[Windows フォーム リソース エディター (Winres.exe)](../../../docs/framework/tools/winres-exe-windows-forms-resource-editor.md) を使ってローカライズできます。</span><span class="sxs-lookup"><span data-stu-id="6b6d0-147">Use Visual Studio to create Windows Forms dialog boxes, so that they can be localized using the [Windows Forms Resource Editor (Winres.exe)](../../../docs/framework/tools/winres-exe-windows-forms-resource-editor.md).</span></span> <span data-ttu-id="6b6d0-148">Windows フォームのダイアログ ボックスを手動でコーディングしないでください。</span><span class="sxs-lookup"><span data-stu-id="6b6d0-148">Do not code Windows Forms dialog boxes by hand.</span></span>  
  
10. <span data-ttu-id="6b6d0-149">専門的なローカライズ (翻訳) 作業を計画してください。</span><span class="sxs-lookup"><span data-stu-id="6b6d0-149">Arrange for professional localization (translation).</span></span>  
  
11. <span data-ttu-id="6b6d0-150">リソースの作成とローカライズについて詳しくは、「[デスクトップ アプリケーションのリソース](../../../docs/framework/resources/index.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="6b6d0-150">For a complete description of creating and localizing resources, see [Resources in Applications](../../../docs/framework/resources/index.md).</span></span>  
  
## <a name="globalization-best-practices-for-aspnet-applications"></a><span data-ttu-id="6b6d0-151">推奨される ASP.NET アプリケーションのグローバライズ手順</span><span class="sxs-lookup"><span data-stu-id="6b6d0-151">Globalization Best Practices for ASP.NET Applications</span></span>  
  
1.  <span data-ttu-id="6b6d0-152"><xref:System.Globalization.CultureInfo.CurrentUICulture%2A> プロパティおよび <xref:System.Globalization.CultureInfo.CurrentCulture%2A> プロパティをアプリケーションで明示的に設定します。</span><span class="sxs-lookup"><span data-stu-id="6b6d0-152">Explicitly set the <xref:System.Globalization.CultureInfo.CurrentUICulture%2A> and <xref:System.Globalization.CultureInfo.CurrentCulture%2A> properties in your application.</span></span> <span data-ttu-id="6b6d0-153">既定値には依存しないでください。</span><span class="sxs-lookup"><span data-stu-id="6b6d0-153">Do not rely on defaults.</span></span>  
  
2.  <span data-ttu-id="6b6d0-154">ASP.NET アプリケーションはマネージ アプリケーションであり、カルチャに基づいた情報の取得、表示、および操作では、ほかのマネージ アプリケーションと同じクラスを使用できます。</span><span class="sxs-lookup"><span data-stu-id="6b6d0-154">Note that ASP.NET applications are managed applications and therefore can use the same classes as other managed applications for retrieving, displaying, and manipulating information based on culture.</span></span>  
  
3.  <span data-ttu-id="6b6d0-155">ASP.NET では次に示す 3 種類のエンコーディングを指定できる点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="6b6d0-155">Be aware that you can specify the following three types of encodings in ASP.NET:</span></span>  
  
    -   <span data-ttu-id="6b6d0-156">requestEncoding は、クライアントのブラウザーから受信されたエンコーディングを指定します。</span><span class="sxs-lookup"><span data-stu-id="6b6d0-156">requestEncoding specifies the encoding received from the client's browser.</span></span>  
  
    -   <span data-ttu-id="6b6d0-157">responseEncoding は、クライアント ブラウザーへ送信するエンコーディングを指定します。</span><span class="sxs-lookup"><span data-stu-id="6b6d0-157">responseEncoding specifies the encoding to send to the client browser.</span></span> <span data-ttu-id="6b6d0-158">ほとんどの場合、このエンコーディングは requestEncoding に指定されたエンコーディングと同一です。</span><span class="sxs-lookup"><span data-stu-id="6b6d0-158">In most situations, this encoding should be the same as that specified for requestEncoding.</span></span>  
  
    -   <span data-ttu-id="6b6d0-159">fileEncoding は、.aspx、.asmx、.asax の各ファイルの解析の既定エンコーディングを指定します。</span><span class="sxs-lookup"><span data-stu-id="6b6d0-159">fileEncoding specifies the default encoding for .aspx, .asmx, and .asax file parsing.</span></span>  
  
4.  <span data-ttu-id="6b6d0-160">ASP.NET アプリケーション内の次の 3 か所で、requestEncoding、responseEncoding、fileEncoding、culture、uiCulture の各属性の値を指定します。</span><span class="sxs-lookup"><span data-stu-id="6b6d0-160">Specify the values for the requestEncoding, responseEncoding, fileEncoding, culture, and uiCulture attributes in the following three places in an ASP.NET application:</span></span>  
  
    -   <span data-ttu-id="6b6d0-161">Web.config ファイルのグローバリゼーション セクション。</span><span class="sxs-lookup"><span data-stu-id="6b6d0-161">In the globalization section of a Web.config file.</span></span> <span data-ttu-id="6b6d0-162">Web.config ファイルは、ASP.NET アプリケーションの外部ファイルです。</span><span class="sxs-lookup"><span data-stu-id="6b6d0-162">This file is external to the ASP.NET application.</span></span> <span data-ttu-id="6b6d0-163">詳しくは、「[\<globalization> 要素](http://msdn.microsoft.com/library/e2dffc8e-ebd2-439b-a2fd-e3ac5e620da7)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="6b6d0-163">For more information, see [\<globalization> Element](http://msdn.microsoft.com/library/e2dffc8e-ebd2-439b-a2fd-e3ac5e620da7).</span></span>  
  
    -   <span data-ttu-id="6b6d0-164">ページ ディレクティブ。</span><span class="sxs-lookup"><span data-stu-id="6b6d0-164">In a page directive.</span></span> <span data-ttu-id="6b6d0-165">アプリケーションがページを処理している時点では、ファイルは既に読み取られています。</span><span class="sxs-lookup"><span data-stu-id="6b6d0-165">Note that, when an application is in a page, the file has already been read.</span></span> <span data-ttu-id="6b6d0-166">そのため、fileEncoding と requestEncoding を指定するには遅すぎます。</span><span class="sxs-lookup"><span data-stu-id="6b6d0-166">Therefore, it is too late to specify fileEncoding and requestEncoding.</span></span> <span data-ttu-id="6b6d0-167">ページ ディレクティブでは uiCulture、Culture、および responseEncoding だけを指定できます。</span><span class="sxs-lookup"><span data-stu-id="6b6d0-167">Only uiCulture, Culture, and responseEncoding can be specified in a page directive.</span></span>  
  
    -   <span data-ttu-id="6b6d0-168">アプリケーション コード (プログラムで指定)。</span><span class="sxs-lookup"><span data-stu-id="6b6d0-168">Programmatically in application code.</span></span> <span data-ttu-id="6b6d0-169">この設定は、要求ごとに変更できます。</span><span class="sxs-lookup"><span data-stu-id="6b6d0-169">This setting can vary per request.</span></span> <span data-ttu-id="6b6d0-170">ページ ディレクティブの場合と同様に、アプリケーション コードの処理時点では、fileEncoding と requestEncoding の指定は遅すぎます。</span><span class="sxs-lookup"><span data-stu-id="6b6d0-170">As with a page directive, by the time the application's code is reached it is too late to specify fileEncoding and requestEncoding.</span></span> <span data-ttu-id="6b6d0-171">アプリケーション コードでは、uiCulture、Culture、および responseEncoding だけを指定できます。</span><span class="sxs-lookup"><span data-stu-id="6b6d0-171">Only uiCulture, Culture, and responseEncoding can be specified in application code.</span></span>  
  
5.  <span data-ttu-id="6b6d0-172">uiCulture 値には、ブラウザー受け入れ言語を設定できます。</span><span class="sxs-lookup"><span data-stu-id="6b6d0-172">Note that the uiCulture value can be set to the browser accept language.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b6d0-173">参照</span><span class="sxs-lookup"><span data-stu-id="6b6d0-173">See Also</span></span>  
 [<span data-ttu-id="6b6d0-174">グローバライズとローカライズ</span><span class="sxs-lookup"><span data-stu-id="6b6d0-174">Globalization and Localization</span></span>](../../../docs/standard/globalization-localization/index.md)  
 [<span data-ttu-id="6b6d0-175">デスクトップ アプリケーションのリソース</span><span class="sxs-lookup"><span data-stu-id="6b6d0-175">Resources in Desktop Apps</span></span>](../../../docs/framework/resources/index.md)

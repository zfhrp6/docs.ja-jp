---
title: "正規表現アクティビティ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b8f24694-49db-4339-92ec-014e3d4ae63b
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: edeb55f25abf9e6f22ebfe1d0ea63eb07ba0f203
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="regular-expression-activities"></a><span data-ttu-id="425b6-102">正規表現アクティビティ</span><span class="sxs-lookup"><span data-stu-id="425b6-102">Regular Expression Activities</span></span>
<span data-ttu-id="425b6-103">このサンプルでは、<xref:System.Text.RegularExpressions> 名前空間の正規表現機能を公開する一連のアクティビティを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="425b6-103">This sample demonstrates how to create a set of activities that expose the regular expression functionality of the <xref:System.Text.RegularExpressions> namespace.</span></span> <span data-ttu-id="425b6-104">このカスタム アクティビティはワークフロー アプリケーション内で使用できます。</span><span class="sxs-lookup"><span data-stu-id="425b6-104">These custom activities can be used within a workflow application.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="425b6-105">正規表現を参照してください[N:System.Text.RegularExpressions](http://go.microsoft.com/fwlink/?LinkId=150434) Namespace です。</span><span class="sxs-lookup"><span data-stu-id="425b6-105"> regular expressions, see [N:System.Text.RegularExpressions](http://go.microsoft.com/fwlink/?LinkId=150434) Namespace.</span></span>  
  
 <span data-ttu-id="425b6-106">次の表に、このサンプルのカスタム アクティビティの詳細を示します。</span><span class="sxs-lookup"><span data-stu-id="425b6-106">The following table details the custom activities in this sample.</span></span>  
  
|<span data-ttu-id="425b6-107">アクティビティ</span><span class="sxs-lookup"><span data-stu-id="425b6-107">Activity</span></span>|<span data-ttu-id="425b6-108">説明</span><span class="sxs-lookup"><span data-stu-id="425b6-108">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="425b6-109">IsMatch</span><span class="sxs-lookup"><span data-stu-id="425b6-109">IsMatch</span></span>|<span data-ttu-id="425b6-110">正規表現で入力文字列内に一致が見つかったかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="425b6-110">Specifies whether the regular expression found a match in the input string.</span></span>|  
|<span data-ttu-id="425b6-111">一致する文字列</span><span class="sxs-lookup"><span data-stu-id="425b6-111">Matches</span></span>|<span data-ttu-id="425b6-112">入力文字列で、正規表現に一致するすべての文字列を検索し、一致した文字列をすべて返します。</span><span class="sxs-lookup"><span data-stu-id="425b6-112">Searches an input string for all occurrences of a regular expression and returns all the successful matches.</span></span>|  
|<span data-ttu-id="425b6-113">Replace</span><span class="sxs-lookup"><span data-stu-id="425b6-113">Replace</span></span>|<span data-ttu-id="425b6-114">指定された入力文字列内で、正規表現パターンに一致する文字列を、指定された置換文字列で置き換えます。</span><span class="sxs-lookup"><span data-stu-id="425b6-114">Within a specified input string, replaces strings that match a regular expression pattern with a specified replacement string.</span></span>|  
  
## <a name="ismatch"></a><span data-ttu-id="425b6-115">IsMatch</span><span class="sxs-lookup"><span data-stu-id="425b6-115">IsMatch</span></span>  
 <span data-ttu-id="425b6-116">`IsMatch` カスタム アクティビティは、`true` 文字列プロパティが `Input` プロパティで指定された正規表現で一致を見つけると、`Pattern` を返します。</span><span class="sxs-lookup"><span data-stu-id="425b6-116">The `IsMatch` custom activity returns `true` if the `Input` string property finds a match in the regular expression specified in the `Pattern` property.</span></span> <span data-ttu-id="425b6-117">このアクティビティは <xref:System.Activities.CodeActivity%601> から派生し、<xref:System.Activities.CodeActivity%601.Execute%2A> メソッド内で、<xref:System.Text.RegularExpressions.Regex.IsMatch%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="425b6-117">The activity derives from <xref:System.Activities.CodeActivity%601> and within the <xref:System.Activities.CodeActivity%601.Execute%2A> method calls the <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> method.</span></span>  
  
 <span data-ttu-id="425b6-118">次の表で、`IsMatch` カスタム アクティビティのプロパティと戻り値について説明します。</span><span class="sxs-lookup"><span data-stu-id="425b6-118">The following table describes the properties and return value for the `IsMatch` custom activity.</span></span>  
  
|<span data-ttu-id="425b6-119">プロパティ値または戻り値</span><span class="sxs-lookup"><span data-stu-id="425b6-119">Property or Return Value</span></span>|<span data-ttu-id="425b6-120">説明</span><span class="sxs-lookup"><span data-stu-id="425b6-120">Description</span></span>|  
|------------------------------|-----------------|  
|<span data-ttu-id="425b6-121">Pattern (必須)</span><span class="sxs-lookup"><span data-stu-id="425b6-121">Pattern (required)</span></span>|<span data-ttu-id="425b6-122">検索に使用する正規表現。</span><span class="sxs-lookup"><span data-stu-id="425b6-122">The regular expression to search with.</span></span>|  
|<span data-ttu-id="425b6-123">Input (必須)</span><span class="sxs-lookup"><span data-stu-id="425b6-123">Input (required)</span></span>|<span data-ttu-id="425b6-124">検索対象の入力文字列。</span><span class="sxs-lookup"><span data-stu-id="425b6-124">The input string to search.</span></span>|  
|<span data-ttu-id="425b6-125">RegexOptions</span><span class="sxs-lookup"><span data-stu-id="425b6-125">RegexOptions</span></span>|<span data-ttu-id="425b6-126">ビットごとの OR の組み合わせ[RegexOptions](http://go.microsoft.com/fwlink/?LinkId=150446)列挙値。</span><span class="sxs-lookup"><span data-stu-id="425b6-126">Bitwise OR combination of [RegexOptions](http://go.microsoft.com/fwlink/?LinkId=150446) enumeration values.</span></span>|  
|<span data-ttu-id="425b6-127">戻り値</span><span class="sxs-lookup"><span data-stu-id="425b6-127">Return value</span></span>|<span data-ttu-id="425b6-128">指定されたパターンで一致が見つかった場合は `true`、それ以外の場合は `false`。</span><span class="sxs-lookup"><span data-stu-id="425b6-128">`true` if the input finds a match in the provided pattern; otherwise `false`.</span></span>|  
  
 <span data-ttu-id="425b6-129">次のコード例は、`IsMatch` カスタム アクティビティの使用方法を示します。</span><span class="sxs-lookup"><span data-stu-id="425b6-129">The following code example demonstrates how to use the `IsMatch` custom activity.</span></span>  
  
```  
new IsMatch  
{  
    Pattern = new InArgument<string>( @"^-?\d+(\.\d{2})?$"),  
    Input = "20.00",  
};  
```  
  
## <a name="matches"></a><span data-ttu-id="425b6-130">一致する文字列</span><span class="sxs-lookup"><span data-stu-id="425b6-130">Matches</span></span>  
 <span data-ttu-id="425b6-131">`Matches` カスタム アクティビティは、入力文字列で、正規表現に一致するすべての文字列を検索し、一致した文字列をすべて返します。</span><span class="sxs-lookup"><span data-stu-id="425b6-131">The `Matches` custom activity searches an input string for all occurrences of a regular expression and returns all the successful matches.</span></span> <span data-ttu-id="425b6-132">このアクティビティは <xref:System.Activities.CodeActivity%601> から派生し、<xref:System.Activities.CodeActivity%601.Execute%2A> メソッド内で、<xref:System.Text.RegularExpressions.Regex.Matches%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="425b6-132">The activity derives from <xref:System.Activities.CodeActivity%601> and within the <xref:System.Activities.CodeActivity%601.Execute%2A> method calls the <xref:System.Text.RegularExpressions.Regex.Matches%2A> method.</span></span>  
  
 <span data-ttu-id="425b6-133">次の表で、`IsMatch` カスタム アクティビティのプロパティと戻り値について説明します。</span><span class="sxs-lookup"><span data-stu-id="425b6-133">The following table describes the properties and return value for the `IsMatch` custom activity.</span></span>  
  
|<span data-ttu-id="425b6-134">プロパティ値または戻り値</span><span class="sxs-lookup"><span data-stu-id="425b6-134">Property or Return Value</span></span>|<span data-ttu-id="425b6-135">説明</span><span class="sxs-lookup"><span data-stu-id="425b6-135">Description</span></span>|  
|------------------------------|-----------------|  
|<span data-ttu-id="425b6-136">Pattern (必須)</span><span class="sxs-lookup"><span data-stu-id="425b6-136">Pattern (required)</span></span>|<span data-ttu-id="425b6-137">検索に使用する正規表現。</span><span class="sxs-lookup"><span data-stu-id="425b6-137">The regular expression to search with.</span></span>|  
|<span data-ttu-id="425b6-138">Input (必須)</span><span class="sxs-lookup"><span data-stu-id="425b6-138">Input (required)</span></span>|<span data-ttu-id="425b6-139">検索対象の入力文字列。</span><span class="sxs-lookup"><span data-stu-id="425b6-139">The input string to search.</span></span>|  
|<span data-ttu-id="425b6-140">RegexOptions</span><span class="sxs-lookup"><span data-stu-id="425b6-140">RegexOptions</span></span>|<span data-ttu-id="425b6-141">ビットごとの OR の組み合わせ[RegexOptions](http://go.microsoft.com/fwlink/?LinkId=150446)列挙値。</span><span class="sxs-lookup"><span data-stu-id="425b6-141">Bitwise OR combination of [RegexOptions](http://go.microsoft.com/fwlink/?LinkId=150446) enumeration values.</span></span>|  
|<span data-ttu-id="425b6-142">戻り値</span><span class="sxs-lookup"><span data-stu-id="425b6-142">Return Value</span></span>|<span data-ttu-id="425b6-143">一致する文字列のコレクションが格納された <xref:System.Text.RegularExpressions.MatchCollection>。</span><span class="sxs-lookup"><span data-stu-id="425b6-143">A <xref:System.Text.RegularExpressions.MatchCollection> that contains the collection of successful matches.</span></span>|  
  
 <span data-ttu-id="425b6-144">次のコード例は、`Matches` カスタム アクティビティの使用方法を示します。</span><span class="sxs-lookup"><span data-stu-id="425b6-144">The following code example demonstrates how to use the `Matches` custom activity.</span></span>  
  
```  
new Matches  
{  
    Pattern = @"\b(?<word>\w+)\s+(\k<word>)\b",  
    Input = "The quick brown fox  fox jumped over over the lazy dog dog.",  
};  
```  
  
## <a name="replace"></a><span data-ttu-id="425b6-145">Replace</span><span class="sxs-lookup"><span data-stu-id="425b6-145">Replace</span></span>  
 <span data-ttu-id="425b6-146">`Replace` カスタム アクティビティは入力文字列を検索し、指定された正規表現と一致するすべての文字列を 1 つの文字列で置き換えます。</span><span class="sxs-lookup"><span data-stu-id="425b6-146">The `Replace` custom activity searches an input string and replaces all strings that match a specified regular expression with a string.</span></span> <span data-ttu-id="425b6-147">このアクティビティは <xref:System.Activities.CodeActivity%601> から派生し、<xref:System.Activities.CodeActivity%601.Execute%2A> メソッド内で、<xref:System.Text.RegularExpressions.Regex.Replace%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="425b6-147">The activity derives from <xref:System.Activities.CodeActivity%601> and within the <xref:System.Activities.CodeActivity%601.Execute%2A> method calls the <xref:System.Text.RegularExpressions.Regex.Replace%2A> method.</span></span>  
  
 <span data-ttu-id="425b6-148">次の表で、`Replace` カスタム アクティビティのプロパティと戻り値について説明します。</span><span class="sxs-lookup"><span data-stu-id="425b6-148">The following table describes the properties and return value for the `Replace` custom activity.</span></span>  
  
|<span data-ttu-id="425b6-149">プロパティ値または戻り値</span><span class="sxs-lookup"><span data-stu-id="425b6-149">Property or Return Value</span></span>|<span data-ttu-id="425b6-150">説明</span><span class="sxs-lookup"><span data-stu-id="425b6-150">Description</span></span>|  
|------------------------------|-----------------|  
|<span data-ttu-id="425b6-151">Pattern (必須)</span><span class="sxs-lookup"><span data-stu-id="425b6-151">Pattern (required)</span></span>|<span data-ttu-id="425b6-152">検索に使用する正規表現。</span><span class="sxs-lookup"><span data-stu-id="425b6-152">The regular expression to search with.</span></span>|  
|<span data-ttu-id="425b6-153">Input (必須)</span><span class="sxs-lookup"><span data-stu-id="425b6-153">Input (required)</span></span>|<span data-ttu-id="425b6-154">検索対象の入力文字列。</span><span class="sxs-lookup"><span data-stu-id="425b6-154">The input string to search.</span></span>|  
|<span data-ttu-id="425b6-155">Replacement</span><span class="sxs-lookup"><span data-stu-id="425b6-155">Replacement</span></span>|<span data-ttu-id="425b6-156">置換文字列。</span><span class="sxs-lookup"><span data-stu-id="425b6-156">The replacement string.</span></span><br /><br /> <span data-ttu-id="425b6-157">`Replacement` が指定されると、`MatchEvaluator` プロパティは無視されます。</span><span class="sxs-lookup"><span data-stu-id="425b6-157">If a `Replacement` is specified, then the `MatchEvaluator` property is ignored.</span></span> <span data-ttu-id="425b6-158">`Replacement` または `MatchEvaluator` のどちらかのプロパティを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="425b6-158">Either the `Replacement` or `MatchEvaluator` property must be set.</span></span>|  
|<span data-ttu-id="425b6-159">MatchEvaluator</span><span class="sxs-lookup"><span data-stu-id="425b6-159">MatchEvaluator</span></span>|<span data-ttu-id="425b6-160">各一致文字列を調べ、元の一致文字列または置換文字列のどちらかを返すカスタム メソッド。</span><span class="sxs-lookup"><span data-stu-id="425b6-160">A custom method that examines each match and returns either the original matched string or a replacement string.</span></span><br /><br /> <span data-ttu-id="425b6-161">`Replacement` が指定されると、`MatchEvaluator` プロパティは無視されます。</span><span class="sxs-lookup"><span data-stu-id="425b6-161">If a `Replacement` is specified, then the `MatchEvaluator` property is ignored.</span></span> <span data-ttu-id="425b6-162">`Replacement` または `MatchEvaluator` のどちらかのプロパティを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="425b6-162">Either the `Replacement` or `MatchEvaluator` property must be set.</span></span>|  
|<span data-ttu-id="425b6-163">RegexOptions</span><span class="sxs-lookup"><span data-stu-id="425b6-163">RegexOptions</span></span>|<span data-ttu-id="425b6-164">ビットごとの OR の組み合わせ[RegexOptions](http://go.microsoft.com/fwlink/?LinkId=150446)列挙値。</span><span class="sxs-lookup"><span data-stu-id="425b6-164">Bitwise OR combination of [RegexOptions](http://go.microsoft.com/fwlink/?LinkId=150446) enumeration values.</span></span>|  
|<span data-ttu-id="425b6-165">戻り値</span><span class="sxs-lookup"><span data-stu-id="425b6-165">Return Value</span></span>|<span data-ttu-id="425b6-166">一致する文字列のコレクションが格納された <xref:System.Text.RegularExpressions.MatchCollection>。</span><span class="sxs-lookup"><span data-stu-id="425b6-166">A <xref:System.Text.RegularExpressions.MatchCollection> that contains the collection of successful matches.</span></span>|  
  
 <span data-ttu-id="425b6-167">次のコード例は、`Replace` カスタム アクティビティの使用方法を示します。</span><span class="sxs-lookup"><span data-stu-id="425b6-167">The following code example demonstrates how to use the `Replace` custom activity.</span></span>  
  
```  
// Using the replacement string.  
new Replace  
{  
    Pattern = @"\bWorld\b",  
    Input = "Hello World! This is a wonderful World",  
    Replacement = "Universe"  
};  
  
// Using a match evaluator.  
new Replace  
{  
    Pattern = new InArgument<string>(pattern),  
    Input = new InArgument<string>(input),  
    MatchEvaluator = new MatchEvaluator(CapText)                  
};  
```  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="425b6-168">このサンプルを使用するには</span><span class="sxs-lookup"><span data-stu-id="425b6-168">To use this sample</span></span>  
  
1.  <span data-ttu-id="425b6-169">[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を使用して、RegexActivities.sln ソリューション ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="425b6-169">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the RegexActivities.sln solution file.</span></span>  
  
2.  <span data-ttu-id="425b6-170">ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。</span><span class="sxs-lookup"><span data-stu-id="425b6-170">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="425b6-171">ソリューションを実行するには、Ctrl キーを押しながら F5 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="425b6-171">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="425b6-172">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="425b6-172">The samples may already be installed on your machine.</span></span> <span data-ttu-id="425b6-173">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="425b6-173">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="425b6-174">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="425b6-174">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="425b6-175">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="425b6-175">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\Regex`  
  
## <a name="see-also"></a><span data-ttu-id="425b6-176">関連項目</span><span class="sxs-lookup"><span data-stu-id="425b6-176">See Also</span></span>

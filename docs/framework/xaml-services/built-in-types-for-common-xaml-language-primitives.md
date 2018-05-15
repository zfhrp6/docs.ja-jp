---
title: 共通の XAML 言語プリミティブの組み込み型
ms.date: 03/30/2017
helpviewer_keywords:
- XAML language primitives [XAML Services]
- XAML [XAML Services], built-in types
- x:String [XAML Services]
- x:TimeSpan [XAML Services]
- x:Byte [XAML Services]
- x:Double [XAML Services]
- XAML [XAML Services], types
- x:Uri [XAML Services]
- XAML built-in types [XAML Services]
- x:Int64 [XAML Services]
- x:Single [XAML Services]
- x:Int32 [XAML Services]
ms.assetid: 11de2f08-5b95-4989-b5ec-5178eb968184
ms.openlocfilehash: 15c359a9a7f9797fc03ce20c453905af01f925d7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="built-in-types-for-common-xaml-language-primitives"></a><span data-ttu-id="cb1a5-102">共通の XAML 言語プリミティブの組み込み型</span><span class="sxs-lookup"><span data-stu-id="cb1a5-102">Built-in Types for Common XAML Language Primitives</span></span>
<span data-ttu-id="cb1a5-103">XAML 2009 では、いくつかのデータ型に対する XAML 言語をサポートします。これらのデータ型は、共通言語ランタイム (CLR: Common Language Runtime) およびその他のプログラミング言語でよく使用されているプリミティブです。</span><span class="sxs-lookup"><span data-stu-id="cb1a5-103">XAML 2009 introduces XAML language-level support for several data types that are frequently used primitives in the common language runtime (CLR) and in other programming languages.</span></span> <span data-ttu-id="cb1a5-104">XAML 2009 でサポートされるようになったのは、 `x:Object`, `x:Boolean`, `x:Char`, `x:String`, `x:Decimal`, `x:Single`, `x:Double`, `x:Int16`, `x:Int32`, `x:Int64`, `x:TimeSpan`, `x:Uri`, `x:Byte`、および `x:Array`の各プリミティブです。</span><span class="sxs-lookup"><span data-stu-id="cb1a5-104">XAML 2009 adds support for these primitives: `x:Object`, `x:Boolean`, `x:Char`, `x:String`, `x:Decimal`, `x:Single`, `x:Double`, `x:Int16`, `x:Int32`, `x:Int64`, `x:TimeSpan`, `x:Uri`, `x:Byte`, and `x:Array`</span></span>  
  
<a name="previous_techniques_for_language_primitives_in_xaml_markup"></a>   
## <a name="previous-techniques-for-language-primitives-in-xaml-markup"></a><span data-ttu-id="cb1a5-105">XAML マークアップの言語プリミティブにおける以前の技術</span><span class="sxs-lookup"><span data-stu-id="cb1a5-105">Previous Techniques for Language Primitives in XAML Markup</span></span>  
 <span data-ttu-id="cb1a5-106">以前の WPF バージョンの XAML では、.NET Framework の CLR プリミティブ定義クラスを含むアセンブリと名前空間をマッピングすることによって、CLR 言語プリミティブを参照していました。</span><span class="sxs-lookup"><span data-stu-id="cb1a5-106">In XAML for previous WPF versions, you could reference the CLR language primitives by mapping the assembly and namespace that contained a CLR primitive definition class for the .NET Framework.</span></span> <span data-ttu-id="cb1a5-107">これらの大半は mscorlib アセンブリおよび <xref:System> 名前空間に含まれています。</span><span class="sxs-lookup"><span data-stu-id="cb1a5-107">Most of these are in the mscorlib assembly and <xref:System> namespace.</span></span> <span data-ttu-id="cb1a5-108">たとえば、 <xref:System.Int32>を使用するには、次のマッピングを宣言します (使用例については、その後に示します)。</span><span class="sxs-lookup"><span data-stu-id="cb1a5-108">For example, to use <xref:System.Int32>, you could declare the following mapping (with an example usage shown thereafter):</span></span>  
  
```  
<Application xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"   
xmlns:sys="clr-namespace:System;assembly=mscorlib">  
  <Application.Resources>  
    <sys:Int32 x:Key="intMeaning">42</sys:Int32>  
  </Application.Resources>  
</Application>  
```  
  
<a name="xaml_2009_language_primitives"></a>   
## <a name="xaml-2009-language-primitives"></a><span data-ttu-id="cb1a5-109">XAML 2009 言語プリミティブ</span><span class="sxs-lookup"><span data-stu-id="cb1a5-109">XAML 2009 Language Primitives</span></span>  
 <span data-ttu-id="cb1a5-110">慣例により、XAML の言語プリミティブとその他すべての XAML 言語要素は、 `x:` プレフィックスを含めて示されます。</span><span class="sxs-lookup"><span data-stu-id="cb1a5-110">By convention, the language primitives for XAML and all other XAML language elements are shown, including the `x:` prefix.</span></span> <span data-ttu-id="cb1a5-111">XAML 言語要素は、実際のマークアップで一般的にこのように使用されます。</span><span class="sxs-lookup"><span data-stu-id="cb1a5-111">This is how XAML language elements are typically used in real-world markup.</span></span> <span data-ttu-id="cb1a5-112">WPF の XAML の概念ドキュメントや XAML 仕様書でも、この規則に従っています。</span><span class="sxs-lookup"><span data-stu-id="cb1a5-112">This convention is followed in the conceptual documentation for XAML in WPF and also in the XAML specification.</span></span>  
  
### <a name="xobject"></a><span data-ttu-id="cb1a5-113">x:Object</span><span class="sxs-lookup"><span data-stu-id="cb1a5-113">x:Object</span></span>  
 <span data-ttu-id="cb1a5-114">CLR バッキングの場合は、 `x:Object` プリミティブは <xref:System.Object>に対応しています。</span><span class="sxs-lookup"><span data-stu-id="cb1a5-114">For CLR backing, the `x:Object` primitive corresponds to <xref:System.Object>.</span></span>  
  
 <span data-ttu-id="cb1a5-115">このプリミティブは通常はアプリケーション マークアップでは使用されず、XAML 型システムで割り当てできるかどうかを確認する場合などに便利です。</span><span class="sxs-lookup"><span data-stu-id="cb1a5-115">This primitive is not typically used in application markup, but might be useful for some scenarios such as checking assignability in a XAML type system.</span></span>  
  
### <a name="xboolean"></a><span data-ttu-id="cb1a5-116">x:Boolean</span><span class="sxs-lookup"><span data-stu-id="cb1a5-116">x:Boolean</span></span>  
 <span data-ttu-id="cb1a5-117">CLR バッキングの場合は、 `x:Boolean` プリミティブは <xref:System.Boolean>に対応しています。</span><span class="sxs-lookup"><span data-stu-id="cb1a5-117">For CLR backing, the `x:Boolean` primitive corresponds to <xref:System.Boolean>.</span></span>  
  
 <span data-ttu-id="cb1a5-118">XAML は、`x:Boolean` の値の大文字と小文字を区別しないで解析します。</span><span class="sxs-lookup"><span data-stu-id="cb1a5-118">XAML parses values for `x:Boolean` as case insensitive.</span></span> <span data-ttu-id="cb1a5-119">`x:Bool` は、承諾済みのプリミティブではありません。</span><span class="sxs-lookup"><span data-stu-id="cb1a5-119">Note that `x:Bool` is not an accepted alternative.</span></span> <span data-ttu-id="cb1a5-120">XAML 言語仕様の定義を参照してください。 [ \[MS-XAML\]セクション 5.2.17 および 5.4.11](http://go.microsoft.com/fwlink/?LinkId=114525)です。</span><span class="sxs-lookup"><span data-stu-id="cb1a5-120">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.17 and 5.4.11](http://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xchar"></a><span data-ttu-id="cb1a5-121">x:Char</span><span class="sxs-lookup"><span data-stu-id="cb1a5-121">x:Char</span></span>  
 <span data-ttu-id="cb1a5-122">CLR バッキングの場合は、 `x:Char` プリミティブは <xref:System.Char>に対応しています。</span><span class="sxs-lookup"><span data-stu-id="cb1a5-122">For CLR backing, the `x:Char` primitive corresponds to <xref:System.Char>.</span></span>  
  
 <span data-ttu-id="cb1a5-123">文字列型および char 型は、XML レベルでファイルの全体的なエンコーディングと相互作用しています。</span><span class="sxs-lookup"><span data-stu-id="cb1a5-123">String and char types have interaction with the overall encoding of the file at the XML level.</span></span> <span data-ttu-id="cb1a5-124">XAML 言語仕様の定義を参照してください。 [ \[MS-XAML\]セクション 5.2.7 および 5.4.1](http://go.microsoft.com/fwlink/?LinkId=114525)です。</span><span class="sxs-lookup"><span data-stu-id="cb1a5-124">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.7 and 5.4.1](http://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xstring"></a><span data-ttu-id="cb1a5-125">x:String</span><span class="sxs-lookup"><span data-stu-id="cb1a5-125">x:String</span></span>  
 <span data-ttu-id="cb1a5-126">CLR バッキングの場合は、 `x:String` プリミティブは <xref:System.String>に対応しています。</span><span class="sxs-lookup"><span data-stu-id="cb1a5-126">For CLR backing, the `x:String` primitive corresponds to <xref:System.String>.</span></span>  
  
 <span data-ttu-id="cb1a5-127">文字列型および char 型は、XML レベルでファイルの全体的なエンコーディングと相互作用しています。</span><span class="sxs-lookup"><span data-stu-id="cb1a5-127">String and char types have interaction with the overall encoding of the file at the XML level.</span></span> <span data-ttu-id="cb1a5-128">XAML 言語仕様の定義を参照してください。 [ \[MS-XAML\]セクション 5.2.6](http://go.microsoft.com/fwlink/?LinkId=114525)です。</span><span class="sxs-lookup"><span data-stu-id="cb1a5-128">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.6](http://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xdecimal"></a><span data-ttu-id="cb1a5-129">x:Decimal</span><span class="sxs-lookup"><span data-stu-id="cb1a5-129">x:Decimal</span></span>  
 <span data-ttu-id="cb1a5-130">CLR バッキングの場合は、 `x:Decimal` プリミティブは <xref:System.Decimal>に対応しています。</span><span class="sxs-lookup"><span data-stu-id="cb1a5-130">For CLR backing, the `x:Decimal` primitive corresponds to <xref:System.Decimal>.</span></span>  
  
 <span data-ttu-id="cb1a5-131">XAML の解析は、本質的に `en-US` カルチャにおいて行われます。</span><span class="sxs-lookup"><span data-stu-id="cb1a5-131">Note that XAML parsing is inherently done under `en-US` culture.</span></span> <span data-ttu-id="cb1a5-132">`en-US` カルチャでは、開発環境または、XAML が実行時に読み込まれる最終的なクライアント ターゲットのカルチャ設定に関係なく、小数コンポーネントの正しい区切り記号は常にピリオド (`.`) です。</span><span class="sxs-lookup"><span data-stu-id="cb1a5-132">Under `en-US` culture, the correct separator for the components of a decimal is always a period (`.`) regardless of culture settings of the development environment, or of the eventual client target where the XAML is loaded at run time.</span></span>  
  
 <span data-ttu-id="cb1a5-133">XAML 言語仕様の定義を参照してください。 [ \[MS-XAML\]セクション 5.2.14 および 5.4.8](http://go.microsoft.com/fwlink/?LinkId=114525)です。</span><span class="sxs-lookup"><span data-stu-id="cb1a5-133">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.14 and 5.4.8](http://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xsingle"></a><span data-ttu-id="cb1a5-134">x:Single</span><span class="sxs-lookup"><span data-stu-id="cb1a5-134">x:Single</span></span>  
 <span data-ttu-id="cb1a5-135">CLR バッキングの場合は、 `x:Single` プリミティブは <xref:System.Single>に対応しています。</span><span class="sxs-lookup"><span data-stu-id="cb1a5-135">For CLR backing, the `x:Single` primitive corresponds to <xref:System.Single>.</span></span>  
  
 <span data-ttu-id="cb1a5-136">数値に加え、`x:Single` のテキスト構文はトークン `Infinity`、`-Infinity`、および `NaN` も許可しています。</span><span class="sxs-lookup"><span data-stu-id="cb1a5-136">In addition to the numeric values, text syntax for `x:Single` also permits the tokens `Infinity`, `-Infinity`, and `NaN`.</span></span> <span data-ttu-id="cb1a5-137">これらのトークンは、大文字と小文字を区別します。</span><span class="sxs-lookup"><span data-stu-id="cb1a5-137">These tokens are treated as case sensitive.</span></span>  
  
 <span data-ttu-id="cb1a5-138">`x:Single` は、テキスト構文の最初の文字が `e` または `E`の場合は、指数表記形式の値をサポートします。</span><span class="sxs-lookup"><span data-stu-id="cb1a5-138">`x:Single` can support values in scientific notation form, if the first character in text syntax is `e` or `E`.</span></span>  
  
 <span data-ttu-id="cb1a5-139">XAML 言語仕様の定義を参照してください。 [ \[MS-XAML\]セクション 5.2.8 および 5.4.2](http://go.microsoft.com/fwlink/?LinkId=114525)です。</span><span class="sxs-lookup"><span data-stu-id="cb1a5-139">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.8 and 5.4.2](http://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xdouble"></a><span data-ttu-id="cb1a5-140">x:Double</span><span class="sxs-lookup"><span data-stu-id="cb1a5-140">x:Double</span></span>  
 <span data-ttu-id="cb1a5-141">CLR バッキングの場合は、 `x:Double` プリミティブは <xref:System.Double>に対応しています。</span><span class="sxs-lookup"><span data-stu-id="cb1a5-141">For CLR backing, the `x:Double` primitive corresponds to <xref:System.Double>.</span></span>  
  
 <span data-ttu-id="cb1a5-142">数値に加え、`x:Double` のテキスト構文は、`Infinity`、`-Infinity`、および `NaN` の各トークンも許可しています。</span><span class="sxs-lookup"><span data-stu-id="cb1a5-142">In addition to the numeric values, text syntax for `x:Double` permits the tokens `Infinity`, `-Infinity`, and `NaN`.</span></span> <span data-ttu-id="cb1a5-143">これらのトークンは、大文字と小文字を区別します。</span><span class="sxs-lookup"><span data-stu-id="cb1a5-143">These tokens are treated as case sensitive.</span></span>  
  
 <span data-ttu-id="cb1a5-144">`x:Double` は指数表記形式の値をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="cb1a5-144">`x:Double` can support values in scientific notation form.</span></span> <span data-ttu-id="cb1a5-145">`e` または `E` という文字を使用して指数部分を示すことができます。</span><span class="sxs-lookup"><span data-stu-id="cb1a5-145">Use the character `e` or `E` to introduce the exponent portion.</span></span>  
  
 <span data-ttu-id="cb1a5-146">XAML 言語仕様の定義を参照してください。 [ \[MS-XAML\]セクション 5.2.9 および 5.4.3](http://go.microsoft.com/fwlink/?LinkId=114525)です。</span><span class="sxs-lookup"><span data-stu-id="cb1a5-146">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.9 and 5.4.3](http://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xint16"></a><span data-ttu-id="cb1a5-147">x:Int16</span><span class="sxs-lookup"><span data-stu-id="cb1a5-147">x:Int16</span></span>  
 <span data-ttu-id="cb1a5-148">CLR バッキングの場合は、 `x:Int16` プリミティブは <xref:System.Int16> に対応し、 `x:Int16` は符号付きとして処理されます。</span><span class="sxs-lookup"><span data-stu-id="cb1a5-148">For CLR backing, the `x:Int16` primitive corresponds to <xref:System.Int16> and `x:Int16` is treated as signed.</span></span> <span data-ttu-id="cb1a5-149">XAML では、テキスト構文に正 (`+`) 符号がない場合でも、暗黙的に正符号値を示しています。</span><span class="sxs-lookup"><span data-stu-id="cb1a5-149">In XAML, the absence of a plus (`+`) sign in text syntax is implied as a positive signed value.</span></span>  
  
 <span data-ttu-id="cb1a5-150">XAML 言語仕様の定義を参照してください。 [ \[MS-XAML\]セクション 5.2.11 および 5.4.5](http://go.microsoft.com/fwlink/?LinkId=114525)です。</span><span class="sxs-lookup"><span data-stu-id="cb1a5-150">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.11 and 5.4.5](http://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xint32"></a><span data-ttu-id="cb1a5-151">x:Int32</span><span class="sxs-lookup"><span data-stu-id="cb1a5-151">x:Int32</span></span>  
 <span data-ttu-id="cb1a5-152">CLR バッキングの場合は、 `x:Int32` プリミティブは <xref:System.Int32>に対応しています。</span><span class="sxs-lookup"><span data-stu-id="cb1a5-152">For CLR backing, the `x:Int32` primitive corresponds to <xref:System.Int32>.</span></span> <span data-ttu-id="cb1a5-153">`x:Int32` は符号付きとして処理されます。</span><span class="sxs-lookup"><span data-stu-id="cb1a5-153">`x:Int32` is treated as signed.</span></span> <span data-ttu-id="cb1a5-154">XAML では、テキスト構文に正 (`+`) 符号がない場合でも、暗黙的に正符号値を示しています。</span><span class="sxs-lookup"><span data-stu-id="cb1a5-154">In XAML, the absence of a plus (`+`) sign in text syntax is implied as a positive signed value.</span></span>  
  
 <span data-ttu-id="cb1a5-155">XAML 言語仕様の定義を参照してください。 [ \[MS-XAML\]セクション 5.2.12 および 5.4.6](http://go.microsoft.com/fwlink/?LinkId=114525)です。</span><span class="sxs-lookup"><span data-stu-id="cb1a5-155">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.12 and 5.4.6](http://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xint64"></a><span data-ttu-id="cb1a5-156">x:Int64</span><span class="sxs-lookup"><span data-stu-id="cb1a5-156">x:Int64</span></span>  
 <span data-ttu-id="cb1a5-157">CLR バッキングの場合は、 `x:Int64` プリミティブは <xref:System.Int64>に対応しています。</span><span class="sxs-lookup"><span data-stu-id="cb1a5-157">For CLR backing, the `x:Int64` primitive corresponds to <xref:System.Int64>.</span></span> <span data-ttu-id="cb1a5-158">`x:Int64` は符号付きとして処理されます。</span><span class="sxs-lookup"><span data-stu-id="cb1a5-158">`x:Int64` is treated as signed.</span></span> <span data-ttu-id="cb1a5-159">XAML では、テキスト構文に正 (`+`) 符号がない場合でも、暗黙的に正符号値を示しています。</span><span class="sxs-lookup"><span data-stu-id="cb1a5-159">In XAML, the absence of a plus (`+`) sign in text syntax is implied as a positive signed value.</span></span>  
  
 <span data-ttu-id="cb1a5-160">XAML 言語仕様の定義を参照してください。 [ \[MS-XAML\]セクション 5.2.13 および 5.4.7](http://go.microsoft.com/fwlink/?LinkId=114525)です。</span><span class="sxs-lookup"><span data-stu-id="cb1a5-160">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.13 and 5.4.7](http://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xtimespan"></a><span data-ttu-id="cb1a5-161">x:TimeSpan</span><span class="sxs-lookup"><span data-stu-id="cb1a5-161">x:TimeSpan</span></span>  
 <span data-ttu-id="cb1a5-162">CLR バッキングの場合は、 `x:TimeSpan` プリミティブは <xref:System.TimeSpan>に対応しています。</span><span class="sxs-lookup"><span data-stu-id="cb1a5-162">For CLR backing, the `x:TimeSpan` primitive corresponds to <xref:System.TimeSpan>.</span></span>  
  
 <span data-ttu-id="cb1a5-163">XAML の時刻-日付形式での解析は、本質的に `en-US` カルチャにおいて行われます。</span><span class="sxs-lookup"><span data-stu-id="cb1a5-163">Note that XAML parsing for time-date format is inherently done under `en-US` culture.</span></span>  
  
 <span data-ttu-id="cb1a5-164">XAML 言語仕様の定義を参照してください。 [ \[MS-XAML\]セクション 5.2.16 および 5.4.10](http://go.microsoft.com/fwlink/?LinkId=114525)です。</span><span class="sxs-lookup"><span data-stu-id="cb1a5-164">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.16 and 5.4.10](http://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xuri"></a><span data-ttu-id="cb1a5-165">x:Uri</span><span class="sxs-lookup"><span data-stu-id="cb1a5-165">x:Uri</span></span>  
 <span data-ttu-id="cb1a5-166">CLR バッキングの場合は、 `x:Uri` プリミティブは <xref:System.Uri>に対応しています。</span><span class="sxs-lookup"><span data-stu-id="cb1a5-166">For CLR backing, the `x:Uri` primitive corresponds to <xref:System.Uri>.</span></span>  
  
 <span data-ttu-id="cb1a5-167">プロトコルのチェックは、 `x:Uri`の XAML 定義の一部ではありません。</span><span class="sxs-lookup"><span data-stu-id="cb1a5-167">Checking for protocols is not part of the XAML definition for `x:Uri`.</span></span>  
  
 <span data-ttu-id="cb1a5-168">XAML 言語仕様の定義を参照してください。 [ \[MS-XAML\]セクション 5.2.15 および 5.4.9](http://go.microsoft.com/fwlink/?LinkId=114525)です。</span><span class="sxs-lookup"><span data-stu-id="cb1a5-168">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.15 and 5.4.9](http://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xbyte"></a><span data-ttu-id="cb1a5-169">x:Byte</span><span class="sxs-lookup"><span data-stu-id="cb1a5-169">x:Byte</span></span>  
 <span data-ttu-id="cb1a5-170">CLR バッキングの場合は、 `x:Byte` プリミティブは <xref:System.Byte>に対応しています。</span><span class="sxs-lookup"><span data-stu-id="cb1a5-170">For CLR backing, the `x:Byte` primitive corresponds to <xref:System.Byte>.</span></span> <span data-ttu-id="cb1a5-171">A <xref:System.Byte>  /  `x:Byte`扱われる符号なしとします。</span><span class="sxs-lookup"><span data-stu-id="cb1a5-171">A <xref:System.Byte> / `x:Byte` is treated as unsigned.</span></span>  
  
 <span data-ttu-id="cb1a5-172">XAML 言語仕様の定義を参照してください。 [ \[MS-XAML\]セクション 5.2.10 および 5.4.4](http://go.microsoft.com/fwlink/?LinkId=114525)です。</span><span class="sxs-lookup"><span data-stu-id="cb1a5-172">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.10 and 5.4.4](http://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xarray"></a><span data-ttu-id="cb1a5-173">x:Array</span><span class="sxs-lookup"><span data-stu-id="cb1a5-173">x:Array</span></span>  
 <span data-ttu-id="cb1a5-174">CLR バッキングの場合は、 `x:Array` プリミティブは <xref:System.Array>に対応しています。</span><span class="sxs-lookup"><span data-stu-id="cb1a5-174">For CLR backing, the `x:Array` primitive corresponds to <xref:System.Array>.</span></span>  
  
 <span data-ttu-id="cb1a5-175">マークアップ拡張構文を使用して配列を XAML 2006 で定義することもできますが、XAML 2009 構文は言語によって定義されたプリミティブであり、マークアップ拡張機能にアクセスする必要がありません。</span><span class="sxs-lookup"><span data-stu-id="cb1a5-175">You can define an array in XAML 2006  by using a markup extension syntax; however, the XAML 2009 syntax is a language-defined primitive that does not require accessing a markup extension.</span></span> <span data-ttu-id="cb1a5-176">XAML 2006 のサポートの詳細については、「 [x:Array Markup Extension](../../../docs/framework/xaml-services/x-array-markup-extension.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cb1a5-176">For more information about XAML 2006 support, see [x:Array Markup Extension](../../../docs/framework/xaml-services/x-array-markup-extension.md).</span></span>  
  
 <span data-ttu-id="cb1a5-177">XAML 言語仕様の定義を参照してください。 [ \[MS-XAML\]セクション 5.2.18](http://go.microsoft.com/fwlink/?LinkId=114525)です。</span><span class="sxs-lookup"><span data-stu-id="cb1a5-177">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.18](http://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
<a name="wpf_support"></a>   
## <a name="wpf-support"></a><span data-ttu-id="cb1a5-178">WPF のサポート</span><span class="sxs-lookup"><span data-stu-id="cb1a5-178">WPF Support</span></span>  
 <span data-ttu-id="cb1a5-179">WPF では XAML 2009 の機能を使用できますが、マークアップ コンパイルされていない XAML に限定されます。</span><span class="sxs-lookup"><span data-stu-id="cb1a5-179">In WPF, you can use XAML 2009 features but only for XAML that is not markup-compiled.</span></span> <span data-ttu-id="cb1a5-180">WPF 向けにマークアップ コンパイルされた XAML、および XAML の BAML 形式は、現在、XAML 2009 のキーワードと機能をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="cb1a5-180">Markup-compiled XAML for WPF and the BAML form of XAML do not currently support the XAML 2009 keywords and features.</span></span>  
  
 <span data-ttu-id="cb1a5-181">WPF と共に XAML 2009 の機能を使用するシナリオは、loose XAML を作成して、WPF ランタイムとオブジェクト グラフにし、その XAML を読み込むかどうか<xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>です。</span><span class="sxs-lookup"><span data-stu-id="cb1a5-181">A scenario where you can use XAML 2009 features together with WPF is if you author loose XAML and you then load that XAML into a WPF runtime and object graph with <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="cb1a5-182">WPF<xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType>とその<xref:System.Windows.Markup.XamlReader.Load%2A>XAML 2009 言語キーワードおよび機能を有効なオブジェクト グラフ表現を処理できます。</span><span class="sxs-lookup"><span data-stu-id="cb1a5-182">The WPF <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> and its <xref:System.Windows.Markup.XamlReader.Load%2A> can process XAML 2009 language keywords and features into a valid object graph representation.</span></span>

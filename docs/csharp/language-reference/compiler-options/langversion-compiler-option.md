---
title: "-langversion (C# コンパイラ オプション)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /langversion
helpviewer_keywords:
- /langversion compiler option [C#]
- -langversion compiler option [C#]
- langversion compiler option [C#]
ms.assetid: 3fb00b05-a0ff-4782-b313-13a4c0f62d94
caps.latest.revision: "33"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 11aab223ee70ff69d8c3470e747738bfe44540ea
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="-langversion-c-compiler-options"></a>-langversion (C# コンパイラ オプション)
コンパイラが、選択した C# 言語仕様に含まれている構文のみを受け入れるようにします。  
  
## <a name="syntax"></a>構文  
  
```console  
-langversion:option  
```  
  
## <a name="arguments"></a>引数  
 `option`  
 有効な値は、次のとおりです。  
  
|オプション|説明|  
|------------|-------------|  
|default|コンパイラは、サポートできるすべての有効な言語の構文を受け入れます。 <sup id="TDefault">[Default](#FDefault)</sup>| 
|ISO-1|コンパイラは、ISO/IEC 23270:2003 C# (1.0/1.1) に含まれている構文のみを受け入れます<sup id="TISO1">[ISO1](#FISO1)</sup>|  
|ISO-2|コンパイラは、ISO/IEC 23270:2006 C# (2.0) に含まれている構文のみを受け入れます<sup id="TISO2">[ISO2](#FISO2)</sup>|
|3|コンパイラは、C# 3.0 以下に含まれている構文のみを受け入れます<sup id="TCS3">[CS3](#FCS3)</sup>|
|4|コンパイラは、C# 4.0 以下に含まれている構文のみを受け入れます<sup id="TCS4">[CS4](#FCS4)</sup>|
|5|コンパイラは、C# 5.0 以下に含まれている構文のみを受け入れます<sup id="TCS5">[CS5](#FCS5)</sup>|
|6|コンパイラは、C# 6.0 以下に含まれている構文のみを受け入れます<sup id="TCS6">[CS6](#FCS6)</sup>|
|7|コンパイラは、C# 7.0 以下に含まれている構文のみを受け入れます<sup id="TCS7">[CS7](#FCS7)</sup>|
|latest|コンパイラは、サポートできるすべての有効な言語の構文を受け入れます。 <sup id="TLatest">[Latest](#FLatest)</sup>|
<!--- Uncomment and move these above
|latest| once they're officially released
|7.1|The compiler accepts only syntax that is included in C# 7.1 or lower <sup id="TCS71">[CS71](#FCS71)</sup>|
|7.2|The compiler accepts only syntax that is included in C# 7.2 or lower <sup id="TCS71">[CS72](#FCS72)</sup>|
|8|The compiler accepts only syntax that is included in C# 8 or lower <sup id="TCS71">[CS8](#FCS8)</sup>|
-->

  
## <a name="remarks"></a>コメント  
 C# アプリケーションで参照されるメタデータは、**-langversion** コンパイラ オプションの対象になりません。  
  
 C# コンパイラのバージョンごとに言語仕様の拡張機能が含まれているため、**-langversion** は、コンパイラの以前のバージョンと同じ機能を提供しません。  
 
 さらに、C# バージョンの更新は、一般的に主要な .Net Framework のリリースと一致しますが、新しい構文および機能は必ずしも特定のフレームワーク バージョンに関連付けられていません。 新機能では、C# リビジョンと共にリリースされる新しいコンパイラの更新プログラムを確実に必要としますが、各特定機能には、独自の最小の .Net API または共通言語ランタイムの要件があり、この要件によって、NuGet パッケージやその他のライブラリを含めることで下位レベルのフレームワークで実行できるようになります。
  
 使用する **-langversion** の設定に関係なく、現在のバージョンの共通言語ランタイムを使用して .exe や .dll を作成します。 1 つの例外は、**-langversion:ISO-1** の下で機能する、フレンド アセンブリと [-moduleassemblyname (C# コンパイラ オプション)](../../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md) です。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのコンパイラ オプションを設定するには  
  
1.  プロジェクトの **[プロパティ]** ページを開きます。  
  
2.  **[ビルド]** プロパティ ページをクリックします。  
  
3.  **[詳細設定]** ボタンをクリックします。  
  
4.  **言語バージョン**プロパティを変更します。  
  
 このコンパイラ オプションをプログラムで設定する方法については、「<xref:VSLangProj80.CSharpProjectConfigurationProperties3.LanguageVersion%2A>」を参照してください。  
    
## <a name="see-also"></a>参照  
 [C# コンパイラ オプション](../../../csharp/language-reference/compiler-options/index.md)  
 [プロジェクトおよびソリューションのプロパティの管理](/visualstudio/ide/managing-project-and-solution-properties)  
 
### <a name="c-language-specification"></a>C# 言語仕様
 [C# 言語仕様リファレンス](../../../csharp/language-reference/language-specification/index.md): .NET Foundation  
 C# 1.0/1.1 [ISO/IEC 23270:2003](https://www.iso.org/standard/36768.html) 情報技術 -- C# 言語仕様: ISO カタログ  
 C# 2.0 [ISO/IEC 23270:2006](https://www.iso.org/standard/42926.html) 情報技術 -- C# 言語仕様: ISO カタログ  
 C# 2.0 [c042926_ISO_IEC_23270_2006(E).zip](http://standards.iso.org/ittf/PubliclyAvailableStandards/c042926_ISO_IEC_23270_2006(E).zip) ISO/IEC 23270:2006 (PDF 形式) : 自由に利用可能な標準 ISO  
 C# 3.0 [CSharp Language Specification.doc](http://download.microsoft.com/download/3/8/8/388e7205-bc10-4226-b2a8-75351c669b09/CSharp%20Language%20Specification.doc) C# 言語仕様バージョン 3.0 : Microsoft Corporation  
 C# 4.0 [Ecma-334.pdf](https://www.ecma-international.org/publications/files/ECMA-ST/Ecma-334.pdf) Standard ECMA-334 4th Edition    
 C# 5.0 [CSharp Language Specification.docx](https://www.microsoft.com/download/details.aspx?id=7029) C# 言語仕様バージョン 5.0 : Microsoft Corporation  
 C# 6.0 [README.md](https://github.com/dotnet/csharplang/blob/master/spec/README.md) C# 言語仕様バージョン 6 - 非公式ドラフト: .NET Foundation  
 C# 7.0 (現在使用できません)  

<!--- Uncomment and add to the above when they become officially released
 C# 7.1 (spec is not yet finished)  
 C# 7.2 (spec is not yet finished)  
 C# 8.0 (spec is not yet finished)  
-->

### <a name="minimum-compiler-version-needed-to-support-all-language-features"></a>すべての言語機能をサポートするために必要な最小コンパイラ バージョン   
[↩](#TDefault)<a name="FDefault">既定</a>、<a name="FISO1">ISO1</a>: Microsoft Visual Studio/Build Tools .Net 2002 またはバンドルされている .Net Framework 1.0 コンパイラ     
[↩](#TISO2)<a name="FISO2">ISO2</a>: Microsoft Visual Studio/Build Tools 2005 またはバンドルされている .Net Framework 2.0 コンパイラ    
[↩](#TCS3)<a name="FCS3">CS3</a>: Microsoft Visual Studio/Build Tools 2008 またはバンドルされている .Net Framework 3.5 コンパイラ    
[↩](#TCS4)<a name="FCS4">CS4</a>: Microsoft Visual Studio/Build Tools 2010 またはバンドルされている .Net Framework 4.0 コンパイラ    
[↩](#TCS5)<a name="FCS5">CS5</a>: Microsoft Visual Studio/Build Tools 2012 またはバンドルされている .Net Framework 4.5 コンパイラ    
[↩](#TCS6)<a name="FCS6">CS6</a>: Microsoft Visual Studio/Build Tools 2015    
[↩](#TCS7)<a name="FCS7">CS7</a>, <a name="FLatest">Latest</a>: Microsoft Visual Studio/Build Tools 2017   

<!--- Uncomment and add to the above when they become officially released
[↩](#TCS71)<a name="FCS71">CS71</a>: Microsoft Visual Studio/Build Tools 20??    
[↩](#TCS72)<a name="FCS72">CS72</a>: Microsoft Visual Studio/Build Tools 20??    
[↩](#TCS8)<a name="FCS71">CS8</a>: Microsoft Visual Studio/Build Tools 20??    
-->

---
title: -langversion (C# コンパイラ オプション)
ms.date: 05/14/2018
f1_keywords:
- /langversion
helpviewer_keywords:
- /langversion compiler option [C#]
- -langversion compiler option [C#]
- langversion compiler option [C#]
ms.assetid: 3fb00b05-a0ff-4782-b313-13a4c0f62d94
ms.openlocfilehash: 2a9501c883fec7478932b22ea2cdcad70865e0fd
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34696287"
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
|default|コンパイラは、最新のメジャー バージョンからサポートできるすべての有効な言語構文を受け入れます。|
|ISO-1|コンパイラは、ISO/IEC 23270:2003 C# (1.0/1.2) に含まれている構文のみを受け入れます<sup id="TISO1">[ISO1](#FISO1)</sup>|  
|ISO-2|コンパイラは、ISO/IEC 23270:2006 C# (2.0) に含まれている構文のみを受け入れます<sup id="TISO2">[ISO2](#FISO2)</sup>|
|3|コンパイラは、C# 3.0 以下に含まれている構文のみを受け入れます<sup id="TCS3">[CS3](#FCS3)</sup>|
|4|コンパイラは、C# 4.0 以下に含まれている構文のみを受け入れます<sup id="TCS4">[CS4](#FCS4)</sup>|
|5|コンパイラは、C# 5.0 以下に含まれている構文のみを受け入れます<sup id="TCS5">[CS5](#FCS5)</sup>|
|6|コンパイラは、C# 6.0 以下に含まれている構文のみを受け入れます<sup id="TCS6">[CS6](#FCS6)</sup>|
|7|コンパイラは、C# 7.0 以下に含まれている構文のみを受け入れます<sup id="TCS7">[CS7](#FCS7)</sup>|
|7.1|コンパイラは、C# 7.1 以下に含まれている構文のみを受け入れます<sup id="TCS71">[CS71](#FCS71)</sup>|
|7.2|コンパイラは、C# 7.2 以下に含まれている構文のみを受け入れます<sup id="TCS72">[CS72](#FCS72)</sup>|
|7.3|コンパイラは、C# 7.3 以下に含まれている構文のみを受け入れます<sup id="TCS73">[CS73](#FCS73)</sup>|
|latest|コンパイラは、サポートできるすべての有効な言語の構文を受け入れます。|

<!--- Uncomment and move these above
|8|The compiler accepts only syntax that is included in C# 8 or lower <sup id="TCS8">[CS8](#FCS8)</sup>|
-->

  
## <a name="remarks"></a>コメント  
 C# アプリケーションで参照されるメタデータは、**-langversion** コンパイラ オプションの対象になりません。  
  
 C# コンパイラのバージョンごとに言語仕様の拡張機能が含まれているため、**-langversion** は、コンパイラの以前のバージョンと同じ機能を提供しません。  
 
 さらに、C# バージョンの更新は、一般的に主要な .NET Framework のリリースと一致しますが、新しい構文および機能は必ずしも特定のフレームワーク バージョンに関連付けられていません。 新機能では、C# リビジョンと共にリリースされる新しいコンパイラの更新プログラムを確実に必要としますが、各特定機能には、独自の最小の .NET API または共通言語ランタイムの要件があり、この要件によって、NuGet パッケージやその他のライブラリを含めることで下位レベルのフレームワークで実行できるようになります。
  
 使用する **-langversion** の設定に関係なく、現在のバージョンの共通言語ランタイムを使用して .exe や .dll を作成します。 1 つの例外は、**-langversion:ISO-1** の下で機能する、フレンド アセンブリと [-moduleassemblyname (C# コンパイラ オプション)](../../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md) です。  
 
 C# 言語バージョンを指定するその他の方法については、「[C# 言語のバージョンの選択](../configure-language-version.md)」のトピックを参照してください。
  
 このコンパイラ オプションをプログラムで設定する方法については、「<xref:VSLangProj80.CSharpProjectConfigurationProperties3.LanguageVersion%2A>」を参照してください。  
    
## <a name="see-also"></a>参照  
 [C# コンパイラ オプション](index.md)  
 [プロジェクトおよびソリューションのプロパティの管理](/visualstudio/ide/managing-project-and-solution-properties)  
 
### <a name="c-language-specification"></a>C# 言語仕様

|Version|リンク|説明|
|-------|----|-----------|
|C# 1.0|[DOC のダウンロード](http://download.microsoft.com/download/a/9/e/a9e229b9-fee5-4c3e-8476-917dee385062/csharp%20language%20specification%20v1.0.doc)|C# 言語仕様バージョン 1.0: Microsoft Corporation|
|C# 1.2|[DOC のダウンロード](http://download.microsoft.com/download/5/e/5/5e58be0a-b02b-41ac-a4a3-7a22286214ff/csharp%20language%20specification%20v1.2.doc)|C# 言語仕様バージョン 1.2: Microsoft Corporation|
|C# 2.0|[PDF のダウンロード](https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/Ecma-334%204th%20edition%20June%202006.pdf)|Standard ECMA-334 4th Edition|
|C# 3.0|[DOC のダウンロード](http://download.microsoft.com/download/3/8/8/388e7205-bc10-4226-b2a8-75351c669b09/CSharp%20Language%20Specification.doc)|C# 言語仕様バージョン 3.0: Microsoft Corporation|
|C# 5.0|[PDF のダウンロード](https://www.ecma-international.org/publications/files/ECMA-ST/Ecma-334.pdf)|Standard ECMA-334 5th Edition|
|C# 6.0|[リンク](../language-specification/index.md)|C# 言語仕様バージョン 6 - 非公式ドラフト: .NET Foundation|
|C# 7.0 以降||現在使用できません|

### <a name="minimum-compiler-version-needed-to-support-all-language-features"></a>すべての言語機能をサポートするために必要な最小コンパイラ バージョン   
[↩](#TISO1)<a name="FISO1">ISO1</a>: Microsoft Visual Studio/Build Tools .Net 2002 またはバンドルされている .Net Framework 1.0 コンパイラ     
[↩](#TISO2)<a name="FISO2">ISO2</a>: Microsoft Visual Studio/Build Tools 2005 またはバンドルされている .Net Framework 2.0 コンパイラ    
[↩](#TCS3)<a name="FCS3">CS3</a>: Microsoft Visual Studio/Build Tools 2008 またはバンドルされている .Net Framework 3.5 コンパイラ    
[↩](#TCS4)<a name="FCS4">CS4</a>: Microsoft Visual Studio/Build Tools 2010 またはバンドルされている .Net Framework 4.0 コンパイラ    
[↩](#TCS5)<a name="FCS5">CS5</a>: Microsoft Visual Studio/Build Tools 2012 またはバンドルされている .Net Framework 4.5 コンパイラ    
[↩](#TCS6)<a name="FCS6">CS6</a>: Microsoft Visual Studio/Build Tools 2015    
[↩](#TCS7)<a name="FCS7">CS7</a>: Microsoft Visual Studio/Build Tools 2017   
[↩](#TCS71)<a name="FCS71">CS71</a>: Microsoft Visual Studio/Build Tools 2017、バージョン 15.3    
[↩](#TCS72)<a name="FCS72">CS72</a>: Microsoft Visual Studio/Build Tools 2017、バージョン 15.5    
[↩](#TCS73)<a name="FCS73">CS73</a>: Microsoft Visual Studio/Build Tools 2017、バージョン 15.7    

<!--- Uncomment and add to the above when they become officially released
[↩](#TCS8)<a name="FCS8">CS8</a>: Microsoft Visual Studio/Build Tools 20??    
-->

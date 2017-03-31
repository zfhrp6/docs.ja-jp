---
title: "-target (C# コンパイラ オプション) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /target
dev_langs:
- CSharp
helpviewer_keywords:
- target compiler options [C#]
- /target compiler options [C#]
- assemblies [C#], compiling
- -target compiler options [C#]
ms.assetid: a18bbd8e-bbf7-49e7-992c-717d0eb1f76f
caps.latest.revision: 22
author: BillWagner
ms.author: wiwagn
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
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 615a0e2993dc78919008e8f9245504a486e2fb77
ms.lasthandoff: 03/13/2017

---
# <a name="target-c-compiler-options"></a>/target (C# コンパイラ オプション)
**/target** コンパイラ オプションは、次の 6 つの形式のいずれかで指定できます。  
  
 [/target:appcontainerexe](../../../csharp/language-reference/compiler-options/target-appcontainerexe-compiler-option.md)  
 [!INCLUDE[win8_appname_long](../../../csharp/includes/win8_appname_long_md.md)] アプリの .exe ファイルを作成する場合。  
  
 [/target:exe](../../../csharp/language-reference/compiler-options/target-exe-compiler-option.md)  
 .exe ファイルを作成する場合。  
  
 [/target:library](../../../csharp/language-reference/compiler-options/target-library-compiler-option.md)  
 コード ライブラリを作成する場合。  
  
 [/target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md)  
 モジュールを作成する場合。  
  
 [/target:winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md)  
 Windows プログラムを作成する場合。  
  
 [/target:winmdobj](../../../csharp/language-reference/compiler-options/target-winmdobj-compiler-option.md)  
 .winmdobj 中間ファイルを作成する場合。  
  
 **/target:module** を指定しない限り、**/target** を使用すると、.NET Framework のアセンブリ マニフェストが出力ファイルに配置されます。 詳細については、「[共通言語ランタイムのアセンブリ](https://msdn.microsoft.com/library/k3677y81)」と「[共通の属性](http://msdn.microsoft.com/library/2f48a7ec-9683-4899-a1d2-a08be8fc558b)」を参照してください。  
  
 アセンブリ マニフェストは、コンパイル中の最初の .exe 出力ファイルに配置されます。.exe 出力ファイルがない場合には、最初の DLL ファイルに配置されます。 たとえば、次のコマンド ラインでは、マニフェストは `1.exe` に配置されます。  
  
```  
csc /out:1.exe t1.cs /out:2.netmodule t2.cs  
```  
  
 コンパイラの 1 回のコンパイルで作成されるアセンブリ マニフェストは 1 つだけです。 コンパイルにおけるすべてのファイルの情報は、アセンブリ マニフェストに含まれます。 **/target:module** で作成されたもの以外のすべての出力ファイルには、アセンブリ マニフェストを含めることができます。 コマンド ラインで複数の出力ファイルを生成する場合は、アセンブリ マニフェストを 1 つだけ作成できます。このアセンブリ マニフェストは、コマンド ラインで指定した最初の出力ファイルに含める必要があります。 最初の出力ファイル (**/target:exe**、**/target:winexe**、**/target:library**、**/target:module**) にかかわらず、同じコンパイルで生成された他の出力ファイルはすべてモジュール (**/target:module**) でなければなりません。  
  
 アセンブリを作成する場合は、<xref:System.CLSCompliantAttribute> 属性を使用して、コードのすべてまたは一部が CLS 準拠であることを指定できます。  
  
```  
// target_clscompliant.cs  
[assembly:System.CLSCompliant(true)]   // specify assembly compliance  
  
[System.CLSCompliant(false)]   // specify compliance for an element  
public class TestClass  
{  
    public static void Main() {}  
}  
```  
  
 このコンパイラ オプションをプログラムで設定する方法の詳細については、「<xref:VSLangProj80.ProjectProperties3.OutputType%2A>」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [C# コンパイラのオプション](../../../csharp/language-reference/compiler-options/index.md)   
 [NIB 方法: プロジェクト プロパティと構成設定を変更する](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)   
 [/subsystemversion (C# コンパイラ オプション)](../../../csharp/language-reference/compiler-options/subsystemversion-compiler-option.md)

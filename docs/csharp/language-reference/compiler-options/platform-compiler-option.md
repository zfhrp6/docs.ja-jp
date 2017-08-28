---
title: "-platform (C# コンパイラ オプション)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /platform
dev_langs:
- CSharp
helpviewer_keywords:
- platform compiler option [C#]
- -platform compiler option [C#]
- /platform compiler option [C#]
ms.assetid: c290ff5e-47f4-4a85-9bb3-9c2525b0be04
caps.latest.revision: 46
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 44d4cadbc45eb141ecb7a83345d2a7a834ce5299
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="platform-c-compiler-options"></a>/platform (C# コンパイラ オプション)
アセンブリを実行できる共通言語ランタイム (CLR) のバージョンを指定します。  
  
## <a name="syntax"></a>構文  
  
```console  
/platform:string  
```  
  
#### <a name="parameters"></a>パラメーター  
 `string`  
 anycpu (既定値)、anycpu32bitpreferred、ARM、x64、x86、または Itanium。  
  
## <a name="remarks"></a>コメント  
  
-   **anycpu** (既定) は、任意のプラットフォーム上で実行できるように、アセンブリをコンパイルします。 可能な場合は、アプリケーションを 64 ビット プロセスとして実行し、32 ビット モードしか使用できない場合は、32 ビットにフォールバックします。  
  
-   **anycpu32bitpreferred** は、任意のプラットフォーム上で実行できるように、アセンブリをコンパイルします。 64 ビットと 32 ビットの両方のアプリケーションをサポートするシステムで、32 ビット モードでアプリケーションを実行します。 このオプションは、.NET Framework 4.5 を対象とするプロジェクトに対してのみ指定できます。  
  
-   **ARM** は、Advanced RISC Machine (ARM) プロセッサ搭載のコンピューター上で実行されるように、アセンブリをコンパイルします。  
  
-   **x64** は、AMD64 または EM64T 命令セットをサポートするコンピューターで 64 ビット共通言語ランタイムにより実行できるように、アセンブリをコンパイルします。  
  
-   **x86** は、32 ビット x86 互換共通言語ランタイムにより実行できるように、アセンブリをコンパイルします。  
  
-   **Itanium** は、Itanium プロセッサを搭載したコンピューターで 64 ビット共通言語ランタイムにより実行できるように、アセンブリをコンパイルします。  
  
 64 ビット Windows オペレーティング システムの場合:  
  
-   **/platform:x86** でコンパイルされたアセンブリは、WOW64 の下で動作する 32 ビット CLR で実行されます。  
  
-   **/platform:anycpu** でコンパイルでされた DLL は、ロード先のプロセスと同じ CLR で実行されます。  
  
-   **/platform:anycpu** でコンパイルされた実行可能ファイルは、64 ビット CLR で実行されます。  
  
-   **/platform:anycpu32bitpreferred** でコンパイルされた実行可能ファイルは、32 ビット CLR で実行されます。  
  
 **anycpu32bitpreferred** 設定は、実行可能 (.EXE) ファイルに対してのみ有効で、.NET Framework 4.5 が必要です。  
  
 Windows 64 ビット オペレーティング システムで実行するアプリケーションの開発に関する詳細は、「[64 ビット アプリケーション](https://msdn.microsoft.com/library/ms241064)」を参照してください。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのコンパイラ オプションを設定するには  
  
1.  プロジェクトの **[プロパティ]** ページを開きます。  
  
2.  **[ビルド]** プロパティ ページをクリックします。  
  
3.  **プラットフォーム ターゲット** プロパティを変更し、.NET Framework 4.5 を対象とするプロジェクトでは、**[32 ビットを優先]** チェック ボックスをオンまたはオフにします。  
  
 **注 /platform** は、Visual C# Express では開発環境で使用できません。  
  
 このコンパイラ オプションをプログラムで設定する方法については、「<xref:VSLangProj80.CSharpProjectConfigurationProperties3.PlatformTarget%2A>」をご覧ください。  
  
## <a name="example"></a>例  
 次の例では、**/platform** オプションを使用して、Windows 64 ビット オペレーティング システムで 64 ビット CLR によりアプリケーションを実行することを指定する方法を示します。  
  
```console  
csc /platform:anycpu filename.cs  
```  
  
## <a name="see-also"></a>関連項目  
 [C# コンパイラのオプション](index.md)   
 [プロジェクトおよびソリューションのプロパティの管理](/visualstudio/ide/managing-project-and-solution-properties)


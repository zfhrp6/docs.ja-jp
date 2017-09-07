---
title: "-win32manifest (C# コンパイラ オプション)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /win32manifest
dev_langs:
- CSharp
helpviewer_keywords:
- /win32manifest compiler option [C#]
- win32manifest compiler option [C#]
- -win32manifest compiler option [C#]
ms.assetid: 9460ea1b-6c9f-44b8-8f73-301b30a01de1
caps.latest.revision: 13
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
ms.openlocfilehash: 938317fdf0c56469b85b1231a47f83e9c2a7d0f2
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="win32manifest-c-compiler-options"></a>/win32manifest (C# コンパイラ オプション)
**/win32manifest** オプションは、プロジェクトのポータブル実行可能 (PE) ファイルに埋め込まれる、ユーザー定義の Win32 アプリケーション マニフェスト ファイルを指定するために使用します。  
  
## <a name="syntax"></a>構文  
  
```console  
/win32manifest: filename  
```  
  
## <a name="arguments"></a>引数  
 `filename`  
 カスタム マニフェスト ファイルの名前と場所。  
  
## <a name="remarks"></a>コメント  
 既定では、 [!INCLUDE[csharp_current_short](~/includes/csharp-current-short-md.md)] コンパイラは "asInvoker" の要求実行レベルを指定するアプリケーション マニフェストを埋め込みます。 マニフェストは、実行可能ファイルがビルドされたフォルダーと同じフォルダーに作成されます (Visual Studio を使用している場合、通常は bin\Debug または bin\Release フォルダー)。 カスタム マニフェストを指定する場合 (たとえば、"highestAvailable" または "requireAdministrator" の要求実行レベルを指定する場合) は、このオプションを使用してファイルの名前を指定します。  
  
> [!NOTE]
>  このオプションと [/win32res (C# コンパイラ オプション)](../../../csharp/language-reference/compiler-options/win32res-compiler-option.md) オプションは、相互に排他的です。 同じコマンド行で両方のオプションを使おうすると、ビルド エラーが返されます。  
  
 アプリケーション マニフェストを持たないアプリケーションは、要求実行レベルを指定した場合、Windows Vista のユーザー アカウント制御機能によって、ファイルまたはレジストリの仮想化の対象となります。 仮想化について詳しくは、「[The Windows Vista Developer Story: Windows Vista Application Development Requirements for User Account Control (UAC)](http://go.microsoft.com/fwlink/?LinkId=95452)」(Windows Vista 開発者ストーリー: ユーザー アカウント制御 (UAC) に関する Windows Vista アプリケーション開発要件) をご覧ください。  
  
 次の条件のいずれかに該当する場合、アプリケーションは仮想化の対象となります。  
  
-   **/nowin32manifest** オプションを使用していて、後のビルド手順でマニフェストを提供していないか、**/win32res** オプションを使用して Windows リソース (.res) ファイルの一部としていない。  
  
-   要求実行レベルが指定されていないカスタム マニフェストを提供している。  
  
 [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] は、既定の .manifest ファイルを作成し、それを実行可能ファイルと一緒にデバッグ ディレクトリとリリースディレクトリに保存します。 カスタム マニフェストを追加するには、任意のテキスト エディターでカスタム マニフェストを作成し、そのファイルをプロジェクトに追加します。 または、**ソリューション エクスプ ローラー**で **[プロジェクト]** アイコンを右クリックし、**[新しい項目の追加]** をクリックして、**[アプリケーション マニフェスト ファイル]** をクリックします。 新規または既存のマニフェスト ファイルを追加すると、そのマニフェストは **[マニフェスト]** ドロップダウン リストに表示されます。 詳しくは、「[[アプリケーション] ページ (プロジェクト デザイナー) (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp)」をご覧ください。  
  
 アプリケーション マニフェストは、カスタムのビルド後手順として提供するか、または [/nowin32manifest (C# コンパイラ オプション)](../../../csharp/language-reference/compiler-options/nowin32manifest-compiler-option.md) オプションを使用して、Win32 リソース ファイルの一部として提供できます。 アプリケーションを Windows Vista でファイルまたはレジストリの仮想化の対象にする場合は、これと同じオプションを使用します。 これにより、コンパイラがポータブル実行可能 (PE) ファイル内に既定のマニフェストを作成し、埋め込むことを回避できます。  
  
## <a name="example"></a>例  
 次の例は、Visual C# コンパイラが PE に挿入する既定のマニフェストを示したものです。  
  
> [!NOTE]
>  コンパイラは、標準のアプリケーション名 "MyApplication.app" を xml に挿入します。 これは、アプリケーションを Windows Server 2003 Service Pack 3 で実行できるようにするための回避策です。  
  
```xml  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
  <assemblyIdentity version="1.0.0.0" name="MyApplication.app"/>  
  <trustInfo xmlns="urn:schemas-microsoft-com:asm.v2">  
    <security>  
      <requestedPrivileges xmlns="urn:schemas-microsoft-com:asm.v3">  
        <requestedExecutionLevel level="asInvoker"/>  
      </requestedPrivileges>  
    </security>  
  </trustInfo>  
</assembly>  
```  
  
## <a name="see-also"></a>関連項目  
 [C# コンパイラのオプション](../../../csharp/language-reference/compiler-options/index.md)   
 [/nowin32manifest (C# コンパイラ オプション)](../../../csharp/language-reference/compiler-options/nowin32manifest-compiler-option.md)   
 [プロジェクトおよびソリューションのプロパティの管理](/visualstudio/ide/managing-project-and-solution-properties)


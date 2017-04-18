---
title: "/win32manifest (Visual Basic) |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- /win32manifest compiler option [Visual Basic]
- win32manifest compiler option [Visual Basic]
- -win32manifest compiler option [Visual Basic]
ms.assetid: 9e3191b4-90db-41c8-966a-28036fd20005
caps.latest.revision: 9
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: b07d5816e5bb80a95e608fa7214a2db48ebac0dc
ms.lasthandoff: 03/13/2017

---
# <a name="win32manifest-visual-basic"></a>/win32manifest (Visual Basic)
プロジェクトのポータブル実行可能 (PE) ファイルに埋め込まれる、ユーザー定義の Win32 アプリケーション マニフェスト ファイルを識別します。  
  
## <a name="syntax"></a>構文  
  
```  
/win32manifest: fileName  
```  
  
## <a name="arguments"></a>引数  
  
|用語|定義|  
|---|---|  
|`fileName`|カスタム マニフェスト ファイルのパス。|  
  
## <a name="remarks"></a>コメント  
 既定では、Visual Basic コンパイラには asInvoker の要求実行レベルを示すアプリケーション マニフェストが埋め込まれます。 実行可能ファイルがビルドされる、通常 Visual Studio を使用する場合は、bin \debug または bin \release フォルダーの同じフォルダーに、マニフェストを作成します。 HighestAvailable または requireAdministrator、要求実行レベルを指定する例については、カスタム マニフェストを指定する場合は、ファイルの名前を指定するこのオプションを使用します。  
  
> [!NOTE]
>  このオプションと[/win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md)オプションは相互に排他的です。 同じコマンド行で両方のオプションを使用しようとする場合は、ビルド エラーが表示されます。  
  
 アプリケーション マニフェストを持たないアプリケーションは、要求実行レベルが Windows Vista のユーザー アカウント制御機能によって、ファイルまたはレジストリの仮想化の対象となりますを指定します。 仮想化の詳細については、次を参照してください。 [Windows Vista の ClickOnce 配置](https://docs.microsoft.com/visualstudio/deployment/clickonce-deployment-on-windows-vista)します。  
  
 次の条件のいずれかが true の場合、アプリケーションは仮想化が適用されます。  
  
1.  使用する、`/nowin32manifest`オプション指定しない後のビルド手順で、または Windows リソース (.res) ファイルの一部としてマニフェストを使用して、`/win32resource`オプション。  
  
2.  要求実行レベルが指定されていないカスタム マニフェストを提供します。  
  
 [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]既定のマニフェスト ファイルを作成し、実行可能ファイルと一緒にデバッグとリリースのディレクトリに格納します。 表示したりをクリックして既定のアプリケーション マニフェスト ファイルを編集**UAC 設定の表示**上、**アプリケーション**プロジェクト デザイナー タブをクリックします。 詳細については、次を参照してください。[アプリケーション ページで、プロジェクト デザイナー) (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/application-page-project-designer-visual-basic)します。  
  
 使用できる、アプリケーション マニフェストまたはカスタムのビルド後の手順として、Win32 リソース ファイルの一部としてを使用して、`/nowin32manifest`オプション。 Windows Vista でファイルまたはレジストリの仮想化を回避できるアプリケーションの場合は、その同じオプションを使用します。 これにより、PE ファイルの既定のマニフェストを作成およびコンパイラができなくなります。  
  
## <a name="example"></a>例  
 次の例では、Visual Basic コンパイラ PE に挿入される既定のマニフェストを示しています。  
  
> [!NOTE]
>  コンパイラは、XML マニフェストに標準のアプリケーション名 MyApplication.app を挿入します。 これは、Windows Server 2003 Service Pack 3 で実行するアプリケーションを有効にする回避策です。  
  
```  
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
 [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)   
 [/nowin32manifest (Visual Basic)](../../../visual-basic/reference/command-line-compiler/nowin32manifest.md)

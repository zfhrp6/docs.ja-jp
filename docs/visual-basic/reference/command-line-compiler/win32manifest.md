---
title: -win32manifest (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- /win32manifest compiler option [Visual Basic]
- win32manifest compiler option [Visual Basic]
- -win32manifest compiler option [Visual Basic]
ms.assetid: 9e3191b4-90db-41c8-966a-28036fd20005
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f81b578c5ee3ffd830cef237fba2272eecd07642
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33654087"
---
# <a name="-win32manifest-visual-basic"></a>-win32manifest (Visual Basic)
プロジェクトのポータブル実行可能 (PE) ファイルに埋め込まれる、ユーザー定義の Win32 アプリケーション マニフェスト ファイルを識別します。  
  
## <a name="syntax"></a>構文  
  
```  
-win32manifest: fileName  
```  
  
## <a name="arguments"></a>引数  
  
|用語|定義|  
|---|---|  
|`fileName`|カスタム マニフェスト ファイルのパス。|  
  
## <a name="remarks"></a>コメント  
 既定では、Visual Basic コンパイラには、asinvoker 要求実行レベルを指定するアプリケーション マニフェストが埋め込まれます。 実行可能ファイルは、ビルド bin \debug か bin \release フォルダー Visual Studio を使用すると、同じフォルダーに、マニフェストを作成します。 HighestAvailable または requireAdministrator、要求実行レベルを指定する例については、カスタム マニフェストを指定する場合は、ファイルの名前を指定するこのオプションを使用します。  
  
> [!NOTE]
>  このオプションおよび[-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md)オプションは相互に排他的です。 同じコマンドラインで両方のオプションを使用しようとすると、ビルド エラーが表示されます。  
  
 アプリケーション マニフェストを持たないアプリケーションは、要求実行レベルを指定した場合、Windows Vista のユーザー アカウント制御機能によって、ファイルまたはレジストリの仮想化の対象となります。 仮想化の詳細については、次を参照してください。 [Windows Vista の ClickOnce 配置](/visualstudio/deployment/clickonce-deployment-on-windows-vista)です。  
  
 アプリケーションは、次の条件のいずれかが true の場合、仮想化されます。  
  
1.  使用する、`-nowin32manifest`オプションに渡さないように後のビルド手順で、または Windows リソース (.res) ファイルの一部としてマニフェストを使用して、`-win32resource`オプション。  
  
2.  要求実行レベルが指定されていないカスタム マニフェストを提供している。  
  
 Visual Studio では、既定のマニフェスト ファイルを作成し、実行可能ファイルと一緒にデバッグとリリースのディレクトリに格納します。 表示またはをクリックして既定のアプリケーション マニフェスト ファイルを編集することができます**UAC 設定の表示**上、**アプリケーション**プロジェクト デザイナーのタブです。 詳細については、「[[アプリケーション] ページ (プロジェクト デザイナー) (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)」を参照してください。  
  
 使用できる、アプリケーション マニフェストまたは Win32 リソース ファイルの一部としてカスタム ビルド後のステップとしてを使用して、`-nowin32manifest`オプション。 アプリケーションを Windows Vista でファイルまたはレジストリの仮想化の対象にする場合は、これと同じオプションを使用します。 これにより、コンパイラからの作成と、PE ファイルの既定のマニフェストを埋め込むことができなくなります。  
  
## <a name="example"></a>例  
 次の例は、Visual Basic コンパイラ PE に挿入される既定のマニフェストを示しています。  
  
> [!NOTE]
>  コンパイラは、標準的なアプリケーション名 MyApplication.app を XML マニフェストに挿入します。 これは、アプリケーションを Windows Server 2003 Service Pack 3 で実行できるようにするための回避策です。  
  
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
 [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-nowin32manifest (Visual Basic)](../../../visual-basic/reference/command-line-compiler/nowin32manifest.md)

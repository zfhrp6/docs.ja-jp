---
title: '方法 : Visual Basic でユーザー設定を永続化する'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], persisting user settings
- persistence [Visual Basic], persisting user settings [Visual Basic]
- user settings [Visual Basic], persisting
ms.assetid: 0e5e6415-b6e2-4602-9be0-a65fa167d007
ms.openlocfilehash: e9d3ab96ffece3c7f441721b90c8c82c734b1405
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33584567"
---
# <a name="how-to-persist-user-settings-in-visual-basic"></a>方法 : Visual Basic でユーザー設定を永続化する
`My.Settings.Save` メソッドを使用して、ユーザー設定の変更を永続化できます。  
  
 通常、アプリケーションでは、ユーザー設定の変更を、アプリケーションのシャットダウン時に永続化するように設計されています。 これは、複数の要因から、設定の保存に数秒かかることがあるためです。  
  
 詳細については、「[My.Settings オブジェクト](../../../../visual-basic/language-reference/objects/my-settings-object.md)」を参照してください。  
  
> [!NOTE]
>  ユーザー スコープ設定の値は実行時に変更および保存できますが、アプリケーション スコープ設定は読み取り専用であり、プログラムで変更することはできません。 アプリケーション スコープの設定を変更するには、アプリケーションを作成するときに、**プロジェクト デザイナー**を使用するか、アプリケーションの構成ファイルを編集します。 詳細については、「[アプリケーションの設定の管理 (.NET)](/visualstudio/ide/managing-application-settings-dotnet)」を参照してください。  
  
## <a name="example"></a>例  
 この例では、`LastChanged` ユーザー設定の値を変更し、`My.Settings.Save` メソッドを呼び出して、その変更を保存します。  
  
 [!code-vb[VbVbalrMyResources#5](../../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/how-to-persist-user-settings_1.vb)]  
  
 この例を動作させるには、アプリケーションに `Date` 型の `LastChanged` ユーザー設定が必要です。 詳細については、「[アプリケーションの設定の管理 (.NET)](/visualstudio/ide/managing-application-settings-dotnet)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [My.Settings オブジェクト](../../../../visual-basic/language-reference/objects/my-settings-object.md)  
 [方法: Visual Basic でアプリケーション設定を読み取る](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)  
 [方法: Visual Basic でユーザー設定を変更する](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)  
 [方法: Visual Basic でユーザー設定のためのプロパティ グリッドを作成する](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)  
 [アプリケーションの設定の管理 (.NET)](/visualstudio/ide/managing-application-settings-dotnet)

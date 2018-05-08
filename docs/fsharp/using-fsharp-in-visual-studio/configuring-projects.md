---
title: プロジェクトの構成 (f#)
description: Visual Studio で f# プロジェクトで作業するときに、プロジェクト デザイナーを使用する方法を説明します。
ms.date: 05/16/2016
ms.openlocfilehash: a6c9539945bbd32748ffca1434c984402bc3f17b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="configuring-projects-in-visual-studio"></a>Visual Studio でプロジェクトを構成します。

> [!NOTE]
この記事は、最新の Visual Studio と最新の状態はありません。  これは更新されます。

このトピックには使用方法に関する情報が含まれています、**プロジェクト デザイナー** f# プロジェクトで作業するときにします。 F# プロジェクトでの作業が Visual Basic または c# のプロジェクトでの作業の大きな違いではありません。 多くの場合、F# で使用すると、一般的な Visual Studio プロジェクトのドキュメントをプライマリ参照として使用できます。 このトピックでは、他の Visual Studio 言語と共有している設定の Visual Studio のドキュメントに関連する情報へのリンクを提供し、f# に固有の設定についても説明します。

## <a name="project-designer"></a>プロジェクト デザイナー
**プロジェクト デザイナー** 、トピックの「一般的な用途の説明を完全に[プロジェクト デザイナーの概要](https://msdn.microsoft.com/library/898dd854-c98d-430c-ba1b-a913ce3c73d7)Visual Studio のマニュアルでします。 **プロジェクト デザイナー**関連する機能によってグループ化されているいくつかのページで構成されます。 F# プロジェクトで使用できるページは、ほとんどの場合の他の言語が使用可能なサブセットです。 F# でサポートされているページは、次の表で説明します。 機能は f# で使用できないか、コマンド ライン オプションを変更することによってのみ使用可能なことに関連して、ページは利用できません。 F# で使用できるページのようになります (C#) ページ最も近いに関連する c# のリンクが提供されるように**プロジェクト デザイナー**ページ。

|プロジェクト デザイナー ページ|関連リンク|説明|
|---------------------|-------------|-----------|
|`Application`|[アプリケーション ページで、プロジェクト デザイナー &#40;C&#35;&#41;](https://msdn.microsoft.com/library/ms247046.aspx)|アプリケーション レベルの設定と、ライブラリまたは実行可能ファイル、アプリケーションが対象とする .NET Framework のバージョン、およびリソースがファイルをに関する情報を作成するかどうかなどのプロパティを指定することができます、アプリケーション使用して、格納されます。|
|`Build`|[[ビルド] ページ (プロジェクト デザイナー) &#40;C&#35;&#41;](https://msdn.microsoft.com/library/kb4wyys2.aspx)|使用すると、コードをコンパイルする方法を制御できます。|
|`Build Events`|[ビルド イベント ページ (プロジェクト デザイナー) &#40;C&#35;&#41;](https://msdn.microsoft.com/library/kb4wyys2.aspx)|使用すると、コンパイル時の前後に実行するコマンドを指定できます。|
|`Debug`|[[デバッグ] ページ (プロジェクト デザイナー)](https://msdn.microsoft.com/library/2wcdezs5.aspx)|デバッグ中にアプリケーションを実行する方法を制御できます。 新機能が含まれます、アプリケーションの開始ディレクトリを使用するコマンドラインと特殊なデバッグ モードをネイティブ コードと SQL など、有効にします。|
|`Reference Paths`|[プロジェクト内の参照の管理](/visualstudio/ide/managing-references-in-a-project)|使用すると、コードが依存しているアセンブリを検索する場所を指定します。|

## <a name="f-specific-settings"></a>F# の特定の設定
次の表は、f# に固有の設定をまとめます。

|プロジェクト デザイナー ページ|設定|説明|
|---------------------|-------|-----------|
|`Build`|`Generate tail calls`|選択した場合、末尾の Microsoft intermediate language (MSIL) の命令の使用を有効にします。 これにより、スタック フレームが tail 再帰関数で再利用されます。 等価の`--tailcalls`コンパイラ オプション。|
|`Build`|`Other flags`|追加のコンパイラ コマンド ライン オプションを指定できます。|

## <a name="see-also"></a>関連項目
 [F# では、Visual Studio での概要します。](../get-started/get-started-visual-studio.md)  
 [コンパイラ オプション](../language-reference/compiler-options.md)  
 [プロジェクト デザイナーの概要](https://msdn.microsoft.com/library/898dd854-c98d-430c-ba1b-a913ce3c73d7(v=vs.100))

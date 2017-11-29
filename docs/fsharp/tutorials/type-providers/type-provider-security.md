---
title: "型プロバイダーのセキュリティ"
description: "F# で型プロバイダーの信頼の設定を変更する方法を含む型プロバイダーのセキュリティについて説明します。"
keywords: "visual f#, f#, 関数型プログラミング"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 9c5a8a1f-5a31-490d-83c0-8beabda75c78
ms.openlocfilehash: c8f03ee90d4dce1d3484a9dfe8951d500d509a2b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="type-provider-security"></a>型プロバイダーのセキュリティ

型プロバイダーはアセンブリ (Dll) の f# プロジェクトまたはスクリプトによって参照される外部データ ソースに接続し、f# 型の環境にこの型情報を提示するコードを含むです。 通常は、コンパイル時し、コードを実行 (または、スクリプトの場合、f# Interactive にコードを送信します)、参照されたアセンブリ内のコードは実行のみ。 ただし、型プロバイダー アセンブリは、エディターでコードが参照されるだけで、Visual Studio で実行されます。 これは、型プロバイダーは、クイック ヒントのツールヒント、IntelliSense 入力候補などのエディターに余分な情報の追加を実行する必要があるために発生します。 その結果、余分なセキュリティの種類に関する考慮事項プロバイダー アセンブリが、Visual Studio プロセス内に自動的に実行されるためです。


## <a name="security-warning-dialog"></a>セキュリティ警告 ダイアログ ボックス
を最初に、特定の型プロバイダー アセンブリを使用する場合、Visual Studio には、を実行する型プロバイダーがあることを警告するセキュリティのダイアログ ボックスが表示されます。 Visual Studio で、型プロバイダーが読み込まれる前に、使用する、この特定のプロバイダーを信頼できるかどうかを決定することができます。 型プロバイダーのソースを信頼する場合は、「この型プロバイダーが信頼されます」ですを選択し、 型プロバイダーのソースを信頼していない場合は、「は信頼できないこの型プロバイダーです」を選択し、 プロバイダーを信頼する、Visual Studio 内で実行し IntelliSense を提供し、機能を構築できます。 そのコードを実行すると、コンピューターが侵害でした型プロバイダー自体が悪意のある場合は、します。

プロジェクトを信頼しないこと、ダイアログ ボックスで選択した型プロバイダーを参照するコードが含まれている場合、コンパイル時に、コンパイラ エラーが報告されます型プロバイダーが信頼されていないことを示すです。 信頼されていない型プロバイダーに依存する任意の種類は、赤の波線で示されます。 コード エディターで参照する安全です。

を直接 Visual Studio での信頼設定を変更する場合は、次の手順を実行します。


#### <a name="to-change-the-trust-settings-for-type-providers"></a>型プロバイダーの信頼の設定を変更するには

1. `Tools`メニューの `Options`を展開し、`F# Tools`ノード。
<br />

2. 選択`Type Providers`、型プロバイダーの一覧で、信頼すると、型プロバイダーのチェック ボックスをオンおよび信頼できないもののチェック ボックスをオフにします。
<br />


## <a name="see-also"></a>関連項目
[型プロバイダー](index.md)

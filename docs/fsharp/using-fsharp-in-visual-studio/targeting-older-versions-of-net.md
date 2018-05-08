---
title: Windows 8 での .NET Framework 2.0 の指定
description: F# を使用する場合は、古いバージョンの .NET Framework を対象とするについて説明します。
ms.date: 05/16/2016
ms.openlocfilehash: 9b08cced63b46778a5081d4de710991a6299fd29
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="targeting-older-versions-of-net"></a>以前のバージョンの .NET の対象化

> [!NOTE]
この記事は、最新の Visual Studio と最新の状態はありません。  これは更新されます。

3.0、または 3.5 で、f# のプロジェクトの Windows 8.1 で Visual Studio がインストールされているときに、.NET Framework 2.0 を対象にすると、次のエラーが表示されます。 

```
This project requires the 2.0 F# runtime, but that runtime is not installed.
```

このエラーが発生するよう、次の条件の組み合わせにわかっています。


- Windows 8.1 には、Visual Studio をインストールします。
<br />

- Visual Studio をインストールする前に、.NET Framework 3.5 を有効にしませんでした。
<br />

- プロジェクトでは、.NET Framework 2.0、3.0、または 3.5 を対象します。
<br />

Visual Studio をインストールするときに、インストールされている、.NET Framework のバージョンを検出し、.NET Framework 3.5 がインストールされ有効になっている場合にのみ、f# 2.0 ランタイムをインストールします。


## <a name="resolving-the-error"></a>エラーの解決
このエラーを解決するには、いずれかの対象 .NET Framework の新しいバージョンを実行できますしたりできます Windows 8.1 での .NET Framework 3.5 を有効にすると Visual Studio のセットアップ プログラムを実行して、f# 2.0 ランタイムをインストール、**修復**オプション。


#### <a name="to-enable-the-net-framework-35-on-windows-81"></a>Windows 8.1 での .NET Framework 3.5 を有効にするには

1. **開始**画面で、開始し、入力**コントロール パネルの **です。
<br />  その名前を入力すると、**コントロール パネルの **下にあるアイコンが表示されます、**アプリ**見出し。
<br />

2. 選択、**コントロール パネル** アイコンを選択、**プログラム** アイコンを選択し、 **Windows の機能のオンまたはオフ**リンクします。
<br />

3. 確認して、 **.NET Framework 3.5 (.NET 2.0 および 3.0 を含む)**  チェック ボックスを選択してを選択し、 **OK**ボタンをクリックします。
<br />  オプションのコンポーネント、.NET Framework の子ノードのチェック ボックスをオンにする必要はありません。
<br />  .NET Framework 3.5 は、既になっていない場合に有効です。
<br />


#### <a name="to-install-the-f-20-runtime"></a>F# 2.0 ランタイムをインストールするには

1. コントロール パネル で、**プログラム**リンクをクリックして、**プログラムと機能**リンクします。
<br />

2. インストールされているプログラムの一覧をインストールし、Visual Studio のエディションを選択、**変更**ボタンをクリックします。
<br />

3. セットアップが起動したら、選択、**修復**ボタンをクリックします。
<br />  詳細については、次を参照してください。 [Visual Studio のインストール](https://msdn.microsoft.com/library/e2h7fzkw.aspx)です。
<br />
## <a name="see-also"></a>関連項目
[Visual F#](../index.md)

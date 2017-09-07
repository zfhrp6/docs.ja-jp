---
title: "Winres.exe (Windows フォーム リソース エディター)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Winres.exe
- Windows Forms Resource Editor
- localization
- Windows Forms, localization
- forms, localizing
- resx files
- .resx files
ms.assetid: cb8bc835-9221-4888-af53-1a4f5fad6c48
caps.latest.revision: 23
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 934373d61407c8cc19b7d6424898a582880f9c21
ms.openlocfilehash: e2a2121d97cd1f7de211a72ed95e2fdf24bfac60
ms.contentlocale: ja-jp
ms.lasthandoff: 08/10/2017

---
# <a name="winresexe-windows-forms-resource-editor"></a>Winres.exe (Windows フォーム リソース エディター)
Windows フォーム リソース エディター (Winres.exe) は、ビジュアル レイアウト ツールです。ローカリゼーションの専門家は、このツールにより、Windows フォームのユーザー インターフェイス (UI: User Interface) で使用されるリソースをローカライズできます。 Winres.exe への入力として使用される .resx ファイルおよび .resources ファイルは、Microsoft Visual Studio などのビジュアル デザイン環境を使用して作成できます。 .NET Framework アプリケーションにおけるリソースの配置については、「[デスクトップ アプリケーションのリソース](../../../docs/framework/resources/index.md)」を参照してください。  
  
 このツールは、Visual Studio と共に自動的にインストールされます。 このツールを実行するには、開発者コマンド プロンプト (または、Windows 7 の Visual Studio コマンド プロンプト) を使用します。 詳細については、「[コマンド プロンプト](../../../docs/framework/tools/developer-command-prompt-for-vs.md)」を参照してください。  
  
 コマンド プロンプトに次のように入力します。  
  
## <a name="syntax"></a>構文  
  
```  
winres resourceFile   
winres /?   
```  
  
## <a name="remarks"></a>コメント  
  
|引数|説明|  
|--------------|-----------------|  
|`resourceFile`|ローカライズするリソース ファイル。 このファイルは Visual Studio デザイナーで作成した、Windows フォームの .resx ファイルまたは .resources ファイルである必要があります。 Winres.exe では、汎用的な .resx ファイルまたは .resources ファイルは開くことができません。|  
  
|オプション|説明|  
|------------|-----------------|  
|**/?**|このツールのコマンド構文とオプションを表示します。|  
  
 Windows フォーム プロジェクトのフォームの UI 要素の状態は、通常、リソース ファイルに格納されます。リソース ファイルは、拡張子 .resx を持つ XML ベースのファイル、または、これに対応する、拡張子 .resources が設定された、コンパイル済みのバイナリ形式のファイルのいずれかです。 Winres.exe ツールでは、上記いずれかの形式のファイルを、Visual Studio のデザイン環境を使用しないで編集できますが、制限があります。 具体的には、以下の編集操作を行うことができます。  
  
-   ニュートラルまたは特定のカルチャ リソース ファイルを編集して、テキスト、サイズ、位置など、フォームやそのコントロールの UI プロパティを変更できます。  
  
-   ニュートラルまたは特定のカルチャのリソース ファイルを、既定のリソース ファイルから作成できます。  
  
-   カルチャ リソース ファイルを別のカルチャのリソース ファイルとして保存できます。 たとえば、英語 (U.S.) のリソース ファイルを、ポーランド語のリソース ファイルとして保存できます。 通常は、新しいファイルを引き続き編集して、新しいカルチャに対応させます。  
  
 「[ローカリゼーション用リソースの階層編成](http://msdn.microsoft.com/library/756hydy4\(v=vs.110\))」または「[ローカリゼーション用リソースの階層編成](http://msdn.microsoft.com/library/756hydy4\(v=vs.120\))」も参照してください。  
  
 Winres.exe では、対応する .resources ファイルに .resx ファイルを変換できません。この場合は Resgen.exe ツールを使用してください。 Resgen.exe について詳しくは、「[Resgen.exe (リソース ファイル ジェネレーター)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md)」を参照してください。  
  
 Winres.exe はグラフィカル アプリケーションであり、ソース コードにアクセスすることなく、リソース ファイルだけを使用して、Windows フォームのデザイン時バージョンを再作成できます。 Winres.exe は、Visual Studio の Windows フォーム デザイナーおよび [プロパティ] ウィンドウを管理します。 この機能を使用すると、Windows フォームが含まれている .resources ファイルや .resx ファイルをビジュアル編集できます。 Winres.exe でのローカライズでは、通常、コントロールのラベルを編集し、ターゲット カルチャに合わせてローカライズしたラベルが納まるようにコントロールの位置とサイズを調整できます。  
  
 Winres.exe がコントロールの型を解決できない場合、ローカライズされた .resx ファイルまたは .resources ファイルには、プレースホルダー コントロールが作成されます。 このプレースホルダー コントロールは、Windows フォーム上にハッチ ウィンドウとして表示されます。 このハッチ ウィンドウのサイズおよび位置は、実際のコントロールのサイズおよび位置と一致します。 プレースホルダー コントロールのプロパティでローカライズできるプロパティは、すべて [プロパティ] ウィンドウに表示されます。 プレースホルダー コントロールに対して行ったすべての変更内容が、実際のコントロールに保存されます。  
  
## <a name="winresexe-versus-visual-studio"></a>Winres.exe と Visual Studio の比較  
 通常、アプリケーションの Windows フォームのローカライズを開始する前に、ローカリゼーション ツールとして Visual Studio と Winres.exe のどちらを使用するのかを決定する必要があります。 この後で説明するバージョンの互換性の問題が原因で、途中でツールを切り替えることができない場合があるためです。  
  
 Visual Studio の利点は、アプリケーションの開発にもローカライズにも使用できる点です。 フォームをローカライズするには、開発を完了してから、プロパティ エディターの **Localizable** プロパティでフォームの <xref:System.ComponentModel.LocalizableAttribute> を `true` に設定し、**Language** プロパティを目的のカルチャに変更します。 次に、文字列を編集し、ターゲット カルチャに合わせて変更した文字列が納まるようにコントロールの位置およびサイズを調整します。 ローカライズ済み .resx file を保存するときに、Visual Studio は、ローカライズ可能なプロパティ (ターゲット カルチャで変更したプロパティ) だけをファイルに書き込みます。 Visual Studio は、ローカライズ済み .resx ファイル用のサテライト アセンブリを正しいディレクトリ位置に自動的に作成します。  「[チュートリアル: Windows フォームのローカリゼーション](http://msdn.microsoft.com/library/y99d1cd3\(v=vs.110\))」も参照してください。  
  
 Visual Studio は、開発およびローカリゼーション用の統合環境を提供しますが、ローカリゼーションがサードパーティのローカライザーによって行われる場合には Winres.exe をツールとして使用することを推奨します。 Winres.exe はローカリゼーション専用のツールであるため、アプリケーションのコードとローカライズ対象のフォームを明確に分離でき、大規模なプロジェクトを管理するうえでより実用的です。  
  
## <a name="using-winresexe"></a>Winres.exe の使用  
 Winres.exe でローカライズを行う場合は、まず、Visual Studio のフォーム デザイナーなどのビジュアル デザイナーを使用してアプリケーションを開発する必要があります。 開発が完了したら、プロパティ エディターの **Localizable** プロパティでフォームの <xref:System.ComponentModel.LocalizableAttribute> を `true` に設定し、既定のカルチャの .resx ファイルを、サードパーティのローカライザーに渡します。 この .resx ファイルには、Winres.exe が元のフォームのデザイン時バージョンを再作成するために使用する補足情報が含まれています。  
  
> [!CAUTION]
>  Winres.exe で既定のリソース ファイルを編集することはできません。 Winres.exe では、変更されたすべてのプロパティがローカライズされたプロパティと解釈され、ターゲット カルチャ リソース ファイルに保存されます。  
  
 カルチャ リソース ファイルの最終バージョンが完成したら、これを使用して、アプリケーションのローカライズ バージョンを作成できます。 詳細については、「[デスクトップ アプリケーションのリソース](../../../docs/framework/resources/index.md)」を参照してください。  
  
 Winres.exe バージョン 2.0 には、以下の機能があります。  
  
-   Winres は、単一ファイル モード (SFM: Single File Mode) または Visual Studio ファイル モード (VSFM: Visual Studio File Mode) で使用できます。 SFM は、フォームとその内容についての情報すべてをリソース ファイルに格納する、レガシなモードです。 VSFM では、カルチャの変更点のみがリソース ファイルに格納されます。  
  
-   エラー レポート ウィンドウがインターフェイスに追加されました。メイン ウィンドウの左下に表示されます。  
  
-   ホット キーの重複をチェックできます。[書式] メニューの **[ホット キーの確認]** をクリックします。  
  
## <a name="version-compatibility"></a>バージョンの互換性  
 Visual Studio .NET 2002 と Visual Studio 2005 では、リソース ファイルの形式が変更されたため、Winres.exe もこれに合わせて変更されました。 したがって、原則として、アプリケーションの作成に使用している .NET Framework と共にリリースされた Winres.exe のバージョンを使用する必要があります。 次の表は、互換性のあるバージョンの一覧です。  
  
|Visual Studio|.NET Framework|Winres.exe|  
|-------------------|--------------------|----------------|  
|Visual Studio .NET 2002|1.0|1.0|  
|Visual Studio .NET 2003|1.1|1.1|  
|Visual Studio 2005|2.0|2.0|  
|Visual Studio 2008|3.0 と 3.5|3.0 と 3.5|  
|Visual Studio 2010|4.0|4.0|  
  
 Winres.exe バージョン 2.0 で、古いバージョンのリソース ファイルを開こうとすると、.NET Framework バージョン 2.0 互換の形式にファイルをアップグレードするよう促すメッセージが表示されます。  
  
 バージョン 2.0 より前のバージョンの .NET Framework の場合、Winres.exe および Visual Studio のフォーム デザイナーは、互換性のないカルチャ ニュートラルなリソース ファイルおよびカルチャ固有のリソース ファイルを作成していました。‏ したがって、ローカリゼーション処理を開始した後は、一方のツールだけを使用する必要がありました。 一方、Winres.exe バージョン 2.0 では、Visual Studio ファイル モード (VSFM) が追加されました。 この名前からわかるようにこのモードには互換性があり、このモードで保存したリソース ファイルはどちらのツールでも編集できます。  
  
> [!NOTE]
>  VSFM には、Visual Studio 互換であるという長所がありますが、変更点だけをリソース ファイルに格納するため、Winres.exe で VSFM を使用するには、現在のリソース ファイルの親ファイルが同じディレクトリに存在する必要があります。 たとえば、ドイツ語のリソース ファイル `TestApp.de-DE.resources` を編集している場合は、既定のリソース ファイル `TestApp.resx` が存在する必要があり、ときにはカルチャ ニュートラルなリソース ファイル `TestApp.de.resources` も必要となることがあります。  
  
## <a name="examples"></a>例  
  
#### <a name="to-localize-a-resx-or-resources-file-associated-with-a-form"></a>フォームに関連付けられた .resx ファイルまたは .resources ファイルをローカライズするには  
  
1.  開発者コマンド プロンプトで「`winres`」と入力して、Winres.exe を実行します。  
  
2.  ローカライズするフォームの既定のリソースを開くには、**[ファイル]** メニューの **[開く]** をクリックし、開くファイルを指定します。  
  
     または  
  
     Winres.exe を起動するときに、コマンド ラインで開くファイルを指定します。  
  
     次のコマンドは、Winres.exe を起動し、`TestApp.resx` に関連付けられたフォームをフォーム デザイナーに読み込みます。  
  
    ```  
    winres TestApp.resx  
    ```  
  
     次のコマンドは、Winres.exe を起動し、`TestApp.resources` に関連付けられたフォームをフォーム デザイナーに読み込みます。  
  
    ```  
    winres TestApp.resources  
    ```  
  
    > [!NOTE]
    >  リソースが編集中であるフォームが他のフォームを継承したフォームである場合は、継承したフォームを含むアセンブリと、継承元 (派生元) のフォームを含むアセンブリの両方が、グローバル アセンブリ キャッシュ (GAC: Global Assembly Cache) に登録されているか、WinRes.exe と同じディレクトリに存在する必要があります。 .NET Framework のコンポーネントを GAC にインストールする方法の詳細については、「[グローバル アセンブリ キャッシュ](../../../docs/framework/app-domains/gac.md)」を参照してください。  
  
3.  フォーム上のコントロールを選択し、このコントロールの <xref:System.Windows.Forms.Control.Text%2A> などのプロパティを変更して、ローカライズ後のカルチャおよび言語を反映します。 ローカライズされたテキストが納まるように、必要に応じてコントロールを移動したりそのサイズを変更したりします。  
  
4.  ローカライズしたバージョンの .resx ファイルや .resources ファイルを保存するには、**[上書き保存]** ボタンをクリックするか、**[ファイル]** メニューの [上書き保存] をクリックします。 **[カルチャを選択する]** ウィンドウが表示されます。  
  
5.  適切なカルチャおよびファイル モードを選択し、**[OK]** をクリックします。 ファイルは、ローカライズ後のリソース ファイルで予測される名前付け規則を使用して保存されます。 たとえば、`TestApp.resources` をドイツのドイツ語用にローカライズする場合、ファイルは `TestApp.de-DE.resources` という名前で保存されます。 `TestApp.resx` をドイツのドイツ語用にローカライズする場合、ファイルは `TestApp.de-DE.resx` という名前で保存されます。 リソースの名前付け規則について詳しくは、「[リソースのパッケージ化と配置](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)」を参照してください。 ランタイムで使用される定義済みカルチャ名の一覧については、「<xref:System.Globalization.CultureInfo> クラス」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ComponentModel.LocalizableAttribute>   
 <xref:System.Globalization.CultureInfo>   
 <xref:System.Resources.ResourceManager>   
 <xref:System.Resources.ResourceReader>   
 <xref:System.Resources.ResourceWriter>   
 [ツール](../../../docs/framework/tools/index.md)   
 [デスクトップ アプリケーションのリソース](../../../docs/framework/resources/index.md)   
 [グローバライズとローカライズ](../../../docs/standard/globalization-localization/index.md)


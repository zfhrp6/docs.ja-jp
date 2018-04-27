---
title: 'チュートリアル: Windows API の呼び出し (Visual Basic)'
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- DLLs, calling
- Windows API, walkthroughs
- platform invoke, walkthroughs
- API calls [Visual Basic], walkthroughs [Visual Basic]
- Windows API, calling
- walkthroughs [Visual Basic], API calls
- DllImport attribute, calling Windows API
- Declare statement [Visual Basic], declaring DLL functions
ms.assetid: 9280ca96-7a93-47a3-8d01-6d01be0657cb
caps.latest.revision: 20
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 34bfb732e2d99b259811573a427ae66628c7fc3a
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="walkthrough-calling-windows-apis-visual-basic"></a>チュートリアル: Windows API の呼び出し (Visual Basic)
Windows Api は、Windows オペレーティング システムの一部であるダイナミック リンク ライブラリ (Dll) です。 それらを使用して、タスクを実行するときは、独自の同等のプロシージャを記述することは困難です。 たとえば、という名前の関数は、Windows`FlashWindowEx`をアプリケーションのタイトル バーを薄いおよび濃い網掛けが交互に行うことができます。  
  
 コード内の Windows Api を使用する利点は、含んでいるため、数十個は既に書き込まれている便利な関数の待機しているために使用する開発にかかる時間を保存することができます。 欠点は、Windows Api が困難で動作する厳格問題が生じたときにできることです。  
  
 Windows Api では、相互運用性の特殊なカテゴリを表します。 Windows Api では、マネージ コードを使用しない、組み込みタイプ ライブラリ、および Visual Studio で使用されるものとは異なるデータ型を使用する必要はありません。 これらの相違のための Windows Api は、Windows Api との相互運用、COM オブジェクトではないため、および[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]プラットフォームを使用して実行呼び出すには、または PInvoke です。 プラットフォーム呼び出しはマネージ Dll に実装されているアンマネージ関数を呼び出すコードを有効にするサービスです。 詳細については、次を参照してください。[アンマネージ DLL 関数の使用](../../../framework/interop/consuming-unmanaged-dll-functions.md)です。 Visual Basic で PInvoke を使用するにはいずれかを使用して、`Declare`ステートメントまたは適用する、`DllImport`属性を空のプロシージャです。  
  
 Windows API の呼び出しでは、Visual Basic の以前は、プログラミングの重要な部分はでしたが、Visual Basic .NET で必要なことはほとんどありません。 マネージ コードを使用する必要があります、可能な限り、 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] Windows API の呼び出しではなく、タスクを実行します。 このチュートリアルで使用する必要のある状況についての情報は Windows Api が必要です。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="api-calls-using-declare"></a>API 呼び出しを使用して宣言します。  
 Windows Api を呼び出して最も一般的な方法を使用して、`Declare`ステートメントです。  
  
#### <a name="to-declare-a-dll-procedure"></a>DLL のプロシージャを宣言するには  
  
1.  呼び出し、関数とその引数、引数の型の名前を特定し、値だけでなく、名前とそれを含んでいる DLL の場所を返します。  
  
    > [!NOTE]
    >  Windows Api の詳細については、プラットフォーム SDK の Windows API では、Win32 SDK のマニュアルを参照してください。 Windows Api を使用する定数の詳細については、Windows.h、プラットフォーム SDK に含まれているなどのヘッダー ファイルを調べてください。  
  
2.  クリックして新しい Windows アプリケーション プロジェクトを開く**新規**上、**ファイル**メニューをクリックし、**プロジェクト**です。 **[新しいプロジェクト]** ダイアログ ボックスが表示されます。  
  
3.  選択**Windows アプリケーション**Visual Basic プロジェクト テンプレートの一覧からです。 新しいプロジェクトが表示されます。  
  
4.  次の追加`Declare`関数には、クラスまたはモジュールの DLL を使用します。  
  
     [!code-vb[VbVbalrInterop#9](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_1.vb)]  
  
### <a name="parts-of-the-declare-statement"></a>部分、Declare ステートメント  
 `Declare`ステートメントには、次の要素が含まれています。  
  
#### <a name="auto-modifier"></a>Auto 修飾子  
 `Auto`修飾子が共通言語ランタイムの規則またはエイリアス名 (指定されている場合) に従って、メソッド名に基づく文字列に変換するランタイムに指示します。  
  
#### <a name="lib-and-alias-keywords"></a>Lib とエイリアスのキーワード  
 名前次、`Function`キーワードは、インポートされた関数にアクセスする、プログラムで使用される名前です。 実際の呼び出しには、関数の名前と同じことができます、または任意の有効なプロシージャの名前と、採用を使用することができます、`Alias`の実際の呼び出しには、関数の名前を指定するキーワードです。  
  
 指定して、`Lib`キーワード、呼び出している関数を含んでいる DLL の場所と名前。 Windows システム ディレクトリ内にあるファイルのパスを指定する必要はありません。  
  
 使用して、`Alias`関数の名前を呼び出している場合は、キーワードは、有効な Visual Basic プロシージャ名、またはアプリケーション内の他の項目の名前と競合しています。 `Alias` 呼び出される関数の場合は true。 名前を示します。  
  
#### <a name="argument-and-data-type-declarations"></a>引数とデータ型の宣言  
 引数とそのデータ型を宣言します。 この部分は、Windows で使用されるデータ型は、Visual Studio のデータ型に対応していないために、難しい課題にすることができます。 Visual Basic では、作業の多くは、互換性のあるデータ型と呼ばれるプロセスの引数を変換することで*マーシャ リング*です。 使用して引数をマーシャ リング方法を明示的に制御できる、<xref:System.Runtime.InteropServices.MarshalAsAttribute>属性で定義されている、<xref:System.Runtime.InteropServices>名前空間。  
  
> [!NOTE]
>  以前のバージョンの Visual Basic では、パラメーターを宣言できる`As Any`、つまり、すべてのデータのデータ型を使用できます。 Visual Basic では、すべての特定のデータ型を使用することが必要です`Declare`ステートメントです。  
  
#### <a name="windows-api-constants"></a>Windows API の定数  
 いくつかの引数は、定数の組み合わせです。 たとえば、`MessageBox`このチュートリアルで示す API は、という名前の整数引数を受け取る`Typ`メッセージ ボックスを表示する方法を制御します。 確認するには、これらの定数の数値の値を指定できます、 `#define` WinUser.h ファイル内のステートメント。 一般に、数値は 16 進数で示される電卓を使用してそれらを追加し、10 進数に変換することがします。 感嘆符スタイルの定数を結合する場合など`MB_ICONEXCLAMATION`0x00000030 し、はい/スタイルなし`MB_YESNO`0x00000004、数値を追加して結果を取得する 0x00000034、または 52 の 10 進数。 これらの値をアプリケーションで定数として宣言し、それらを結合することをお勧め、10 進数の結果を直接使用できますを使用して、`Or`演算子。  
  
###### <a name="to-declare-constants-for-windows-api-calls"></a>Windows API の呼び出しのための定数を宣言するには  
  
1.  Windows 関数の呼び出しには、ドキュメントを参照してください。 使用されている定数の名前とこれらの定数の数値を含む .h ファイルの名前を決定します。  
  
2.  メモ帳などのテキスト エディターを使用して、ヘッダー (.h) ファイルの内容を表示しを使用する定数を使用して関連付けられている値を検索します。 たとえば、 `MessageBox` API の定数を使用して`MB_ICONQUESTION`をメッセージ ボックスに疑問符 () を表示します。 定義を`MB_ICONQUESTION`WinUser.h では、次のように表示されます。  
  
     `#define MB_ICONQUESTION             0x00000020L`  
  
3.  該当するショートカットを追加`Const`ステートメントをクラスまたはモジュールがアプリケーションで使用できるこれらの定数を確認します。 例えば:  
  
     [!code-vb[VbVbalrInterop#11](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_2.vb)]  
  
###### <a name="to-call-the-dll-procedure"></a>DLL のプロシージャを呼び出しています  
  
1.  という名前のボタンの追加`Button1`の起動時に、プロジェクトの形式し、すると、そのコードを表示する をダブルクリックします。 ボタンのイベント ハンドラーが表示されます。  
  
2.  コードを追加して、`Click`プロシージャを呼び出すし、適切な引数を提供する、追加したボタンのイベント ハンドラー。  
  
     [!code-vb[VbVbalrInterop#12](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_3.vb)]  
  
3.  F5 キーを押してプロジェクトを実行します。 両方と、メッセージ ボックスが表示**はい**と**いいえ**応答ボタン。 いずれかをクリックします。  
  
#### <a name="data-marshaling"></a>データ マーシャ リング  
 Visual Basic では、パラメーターと Windows API の呼び出しの戻り値のデータ型に自動的に変換しますが、使用することができます、 `MarshalAs` API ものと想定するアンマネージ データ型を明示的に指定する属性。 相互運用マーシャ リングの詳細については、次を参照してください。[相互運用マーシャ リング](../../../framework/interop/interop-marshaling.md)です。  
  
###### <a name="to-use-declare-and-marshalas-in-an-api-call"></a>宣言と MarshalAs API 呼び出しで使用するには  
  
1.  データ型を引数、呼び出す関数の名前を決定する値を返します。  
  
2.  アクセスを簡素化する、`MarshalAs`属性は、追加、`Imports`クラスまたは次の例のように、モジュールのコードの先頭にステートメント。  
  
     [!code-vb[VbVbalrInterop#13](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_4.vb)]  
  
3.  クラスまたはモジュールを使用しているし、適用にインポートした関数の関数プロトタイプを追加、`MarshalAs`属性をパラメーターまたは戻り値。 次の例では、型を要求する API 呼び出し`void*`としてマーシャ リング`AsAny`:  
  
     [!code-vb[VbVbalrInterop#14](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_5.vb)]  
  
## <a name="api-calls-using-dllimport"></a>DllImport を使用して、API 呼び出し  
 `DllImport`属性がタイプ ライブラリを持たない Dll で関数を呼び出す 2 番目の方法を提供します。 `DllImport` 使用するとほぼ同等な`Declare`ステートメントが関数を呼び出す方法より詳細に制御を提供します。  
  
 使用することができます`DllImport`ほとんどの Windows API の呼び出しは、共有を参照している限りを呼び出します (とも呼ばれる*静的*) メソッドです。 クラスのインスタンスを必要とするメソッドを使用することはできません。 異なり`Declare`ステートメント、`DllImport`呼び出しは使用できません、`MarshalAs`属性。  
  
#### <a name="to-call-a-windows-api-using-the-dllimport-attribute"></a>DllImport 属性を使用して Windows API を呼び出す  
  
1.  クリックして新しい Windows アプリケーション プロジェクトを開く**新規**上、**ファイル**メニューをクリックし、**プロジェクト**です。 **[新しいプロジェクト]** ダイアログ ボックスが表示されます。  
  
2.  選択**Windows アプリケーション**Visual Basic プロジェクト テンプレートの一覧からです。 新しいプロジェクトが表示されます。  
  
3.  という名前のボタンの追加`Button2`スタートアップ フォームにします。  
  
4.  ダブルクリックして`Button2`フォームのコード ビューを開きます。  
  
5.  アクセスを簡単に`DllImport`、追加、`Imports`スタートアップ フォーム クラスのコードの先頭にステートメント。  
  
     [!code-vb[VbVbalrInterop#13](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_4.vb)]  
  
6.  空の関数を前の宣言、 `End Class` 、フォーム、名、関数のステートメント`MoveFile`です。  
  
7.  適用、`Public`と`Shared`関数宣言とパラメーターを設定する修飾子`MoveFile`Windows API 関数を使用して、引数に基づきます。  
  
     [!code-vb[VbVbalrInterop#16](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_6.vb)]  
  
     関数は、任意の有効なプロシージャ名前を持つことができます。`DllImport`属性は、DLL の名前を指定します。 相互運用性は、パラメーターのマーシャ リングも処理やデータに類似する Visual Studio のデータ型を選択できるように、戻り値型 API ではあります。  
  
8.  適用、`DllImport`属性を空の関数。 最初のパラメーターを呼び出している関数を含んでいる DLL の場所と名前です。 Windows システム ディレクトリ内にあるファイルのパスを指定する必要はありません。 2 番目のパラメーターは、Windows API では、関数の名前を指定する名前付き引数です。 この例では、`DllImport`属性への呼び出しを強制する`MoveFile`に転送される`MoveFileW`KERNEL32 にします。DLL です。 `MoveFileW`メソッドは、パスからファイルをコピー`src`パスに`dst`です。  
  
     [!code-vb[VbVbalrInterop#17](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_7.vb)]  
  
9. コードを追加して、`Button2_Click`イベント ハンドラーで関数を呼び出します。  
  
     [!code-vb[VbVbalrInterop#18](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_8.vb)]  
  
10. Test.txt という名前のファイルを作成し、ハード ドライブに C:\Tmp ディレクトリに配置します。 必要な場合は、Tmp ディレクトリを作成します。  
  
11. F5 キーを押してアプリケーションを起動します。 メイン フォームが表示されます。  
  
12. をクリックして**Button2**です。 ファイルを移動できる場合は、「ファイルが正常に移動されました」メッセージが表示されます。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Runtime.InteropServices.DllImportAttribute>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [Declare ステートメント](../../../visual-basic/language-reference/statements/declare-statement.md)  
 [Auto](../../../visual-basic/language-reference/modifiers/auto.md)  
 [Alias](../../../visual-basic/language-reference/statements/alias-clause.md)  
 [COM 相互運用](../../../visual-basic/programming-guide/com-interop/index.md)  
 [マネージ コードでのプロトタイプの作成](../../../framework/interop/creating-prototypes-in-managed-code.md)  
 [コールバック メソッドとしてのデリゲートのマーシャ リング](../../../framework/interop/marshaling-a-delegate-as-a-callback-method.md)

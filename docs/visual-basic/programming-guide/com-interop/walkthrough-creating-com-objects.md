---
title: "Walkthrough: Creating COM Objects with Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "COM interop, creating COM objects"
  - "COM objects, creating"
  - "COM interop, walkthroughs"
  - "object creation, COM objects"
  - "COM objects, walkthroughs"
ms.assetid: 7b07a463-bc72-4392-9ba0-9dfcb697a44f
caps.latest.revision: 30
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 30
---
# Walkthrough: Creating COM Objects with Visual Basic
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

新しいアプリケーションまたはコンポーネントを作成する場合は、.NET Framework アセンブリを作成します。  また、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] を使用することで、.NET Framework コンポーネントを COM に公開することもできます。  これにより、COM コンポーネントを必要とする以前のアプリケーション スイートに新しいコンポーネントを作成できるようになります。  このチュートリアルでは、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] を使用して [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] オブジェクトを COM オブジェクトとして公開する方法を、COM クラス テンプレートを使う場合と使わない場合の両方で紹介します。  
  
 COM オブジェクトを公開するための最も簡単な方法は、COM クラス テンプレートを使用する方法です。  COM クラス テンプレートは、新規クラスを作成し、クラスと相互運用レイヤーが COM オブジェクトとして生成されるようにプロジェクトを設定し、生成された COM オブジェクトをオペレーティング システムに登録します。  
  
> [!NOTE]
>  [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] で作成したクラスも、使用するアンマネージ コードの COM オブジェクトとして公開できますが、これは本当の COM オブジェクトではないので、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] では使用できません。  詳細については、「[COM Interoperability in .NET Framework Applications](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)」を参照してください。  
  
 [!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note-settings-general-md.md)]  
  
### COM クラス テンプレートを使用して COM オブジェクトを作成するには  
  
1.  **\[ファイル\]** メニューで **\[新しいプロジェクト\]** をクリックして、新しい Windows アプリケーション プロジェクトを開きます。  
  
2.  **\[プロジェクトの種類\]** フィールドの **\[新しいプロジェクト\]** ダイアログ ボックスで、Windows が選択されていることを確認します。  **テンプレート** ペインの一覧の **\[クラス ライブラリ\]** をクリックし、**\[OK\]** をクリックします。  新しいプロジェクトが表示されます。  
  
3.  **\[プロジェクト\]** メニューの **\[新しい項目の追加\]** をクリックします。  **\[新しい項目の追加\]** ダイアログ ボックスが表示されます。  
  
4.  **テンプレート** ペインの一覧の **\[COM クラス\]** を選択し、**\[追加\]** をクリックします。  [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] によって新しいクラスが追加され、COM 相互運用のための新しいプロジェクトが構成されます。  
  
5.  プロパティ、メソッド、イベントなどのコードを COM クラスに追加します。  
  
6.  **\[ビルド\]** メニューの **\[ClassLibrary1 のビルド\]** をクリックします。  [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] によってアセンブリが作成され、COM オブジェクトがオペレーティング システムに登録されます。  
  
## COM クラス テンプレートを使用しない COM オブジェクトの作成  
 COM クラスは、COM クラス テンプレートを使用しなくても、手動で作成することもできます。  コマンド ラインから操作するときや、COM オブジェクトの定義方法を制御するときに、手動による作業手順が役に立ちます。  
  
#### COM オブジェクトが生成されるようにプロジェクトを設定するには  
  
1.  **\[ファイル\]** メニューで **\[新しいプロジェクト\]** をクリックして、新しい Windows アプリケーション プロジェクトを開きます。  
  
2.  **\[プロジェクトの種類\]** フィールドの **\[新しいプロジェクト\]** ダイアログ ボックスで、Windows が選択されていることを確認します。  **テンプレート** ペインの一覧の **\[クラス ライブラリ\]** をクリックし、**\[OK\]** をクリックします。  新しいプロジェクトが表示されます。  
  
3.  **ソリューション エクスプローラー**で、プロジェクトを右クリックし、**\[プロパティ\]** をクリックします。  **プロジェクト デザイナー** が表示されます。  
  
4.  **\[コンパイル\]** タブをクリックします。  
  
5.  **\[COM の相互運用機能に登録\]** チェック ボックスをオンにします。  
  
#### クラス内のコードを設定して COM オブジェクトを作成するには  
  
1.  **ソリューション エクスプローラー**で、**Class1.vb** をダブルクリックして、そのコードを表示します。  
  
2.  クラスの名前を `ComClass1` に変更します。  
  
3.  `ComClass1` に次の定数を追加します。  これにより、COM オブジェクトに必要な グローバル一意識別子 \(GUID\) 定数が格納されます。  
  
     [!code-vb[VbVbalrInterop#2](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_1.vb)]  
  
4.  **\[ツール\]** メニューの **\[GUID の作成\]** をクリックします。  **\[GUID の作成\]** ダイアログ ボックスで、**\[レジストリ形式\]** をクリックし、**\[コピー\]** をクリックします。  **\[終了\]** をクリックします。  
  
5.  `ClassId` の空白の文字列を GUID で置き換え、前後にある中かっこを削除します。  たとえば、Guidgen によって提供された GUID が `"{2C8B0AEE-02C9-486e-B809-C780A11530FE}"` である場合、コードは次のようになります。  
  
     [!code-vb[VbVbalrInterop#3](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_2.vb)]  
  
6.  次の例のように、`InterfaceId` 定数と `EventsId` 定数に対してこれまでの手順を繰り返します。  
  
     [!code-vb[VbVbalrInterop#4](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_3.vb)]  
  
    > [!NOTE]
    >  COM コンポーネントが他の COM コンポーネントと競合しないよう、GUID が新しく、一意であることを確認する必要があります。  
  
7.  `ComClass` 属性を `ComClass1` に追加して、クラス ID、インターフェイス ID、およびイベント ID のグローバル一意識別子 \(GUID: global unique identifier\) を指定します。次に例を示します。  
  
     [!code-vb[VbVbalrInterop#5](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_4.vb)]  
  
8.  COM クラスにはパラメーターなしの `Public Sub New()` コンストラクターを指定する必要があります。指定しなかった場合、クラスが正しく登録されません。  パラメーターなしのコンストラクターをクラスに追加します。  
  
     [!code-vb[VbVbalrInterop#6](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_5.vb)]  
  
9. プロパティ、メソッド、およびイベントをクラスに追加して、最後に `End Class` ステートメントを記述します。  **\[ビルド\]** メニューの **\[ソリューションのビルド\]** をクリックします。  [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] によってアセンブリが作成され、COM オブジェクトがオペレーティング システムに登録されます。  
  
    > [!NOTE]
    >  [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] で生成した COM オブジェクトは本当の COM オブジェクトではないため、他の [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] アプリケーションでは使用できません。  そのような COM オブジェクトへの参照を追加しようとすると、エラーが発生します。  詳細については、「[COM Interoperability in .NET Framework Applications](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)」を参照してください。  
  
## 参照  
 <xref:Microsoft.VisualBasic.ComClassAttribute>   
 [COM Interop](../../../visual-basic/programming-guide/com-interop/index.md)   
 [Walkthrough: Implementing Inheritance with COM Objects](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)   
 [\#Region Directive](../../../visual-basic/language-reference/directives/region-directive.md)   
 [COM Interoperability in .NET Framework Applications](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)   
 [Troubleshooting Interoperability](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)
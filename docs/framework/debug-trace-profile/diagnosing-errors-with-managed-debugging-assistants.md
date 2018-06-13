---
title: マネージ デバッグ アシスタントによるエラーの診断
ms.date: 03/30/2017
f1_keywords:
- EHMDA
helpviewer_keywords:
- run-time error debugging
- managed code, run-time debugging
- resource debugging
- registry, MDAs
- common language runtime, debugging
- MDAs (managed debugging assistants)
- configuration files [.NET Framework], debugging runtime events
- messages, managed debugging assistants
- application configuration files, managed debugging assistants
- debugging [.NET Framework], managed debugging assistants
- environment variables, MDAs
- access violation debugging [.NET Framework]
- diagnostics, managed debugging assistants
- unmanaged code, run-time debugging
- default debug output stream
- memory, debugging
- app.config files, managed debugging assistants
- managed debugging assistants (MDAs)
- debugging [.NET Framework], run-time errors
- trapping events
- runtime, error debugging
- disabling MDAs
- output, managed debugging assistants
- errors [.NET Framework], managed debugging assistants
ms.assetid: 76994ee6-9fa9-4059-b813-26578d24427c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 16a039a5edb0e1023551f97deefbf7874a19638b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33392321"
---
# <a name="diagnosing-errors-with-managed-debugging-assistants"></a>マネージ デバッグ アシスタントによるエラーの診断
マネージ デバッグ アシスタント (MDA) は、共通言語ランタイム (CLR: Common Language Runtime) と連携してランタイム状態に関する情報を提供するデバッグ支援ツールです。 MDA は、これ以外の方法ではトラップできないランタイム イベントに関する情報メッセージを生成します。 MDA を使用すると、マネージ コードからアンマネージ コードへの遷移時に発生する、検出が難しいアプリケーション バグを分離できます。 すべての MDA を有効または無効にするには、Windows レジストリにキーを追加するか、環境変数を設定します。 特定の MDA を有効にするには、アプリケーション構成設定を使用します。 一部の MDA については、アプリケーションの構成ファイルで追加の構成設定を個別に設定できます。 この構成ファイルはランタイムの読み込み時に解析されるため、MDA は、マネージ アプリケーションが起動する前に有効にする必要があります。 MDA は、既に起動しているアプリケーションに対して有効にできません。  
  
> [!NOTE]
>  MDA を有効にすると、コードをデバッガーで実行していないときでも MDA がアクティブになります。 デバッガーが存在しない場合に MDA イベントが発生した場合、そのイベントはハンドルされない例外とは異なりますが、イベント メッセージはハンドルされない例外のダイアログ ボックスに表示されます。 このダイアログ ボックスが表示されないようにするには、デバッグ環境でコードを実行しているのではないときに、MDA を有効にする設定を削除します。  
  
> [!NOTE]
>  Visual Studio の統合開発環境 (IDE: Integrated Development Environment) でコードを実行している場合は、特定の MDA イベントを示す例外のダイアログ ボックスを表示しないようにできます。 これを行うには、**[デバッグ]** メニューの **[例外]** をクリックします  (**[デバッグ]** メニューに **[例外]** が表示されない場合は、**[ツール]** メニューの **[カスタマイズ]** をクリックし、メニュー項目を追加します)。**[例外]** ダイアログ ボックスで、**[マネージ デバッグ アシスタント]** の一覧を展開し、個々の MDA に対して **[スローされるとき]** チェック ボックスをオフにします。 たとえば、[contextSwitchDeadlock](../../../docs/framework/debug-trace-profile/contextswitchdeadlock-mda.md) の例外のダイアログ ボックスを表示しないようにするには、**[マネージ デバッグ アシスタント]** で、この名前の横にある **[スローされるとき]** チェック ボックスをオフにします。 このダイアログ ボックスを使用して、MDA 例外ダイアログ ボックスの表示を有効にすることもできます。  
  
 .NET Framework に付属する MDA の一覧を次の表に示します。  
  
|||  
|-|-|  
|[asynchronousThreadAbort](../../../docs/framework/debug-trace-profile/asynchronousthreadabort-mda.md)|[bindingFailure](../../../docs/framework/debug-trace-profile/bindingfailure-mda.md)|  
|[callbackOnCollectedDelegate](../../../docs/framework/debug-trace-profile/callbackoncollecteddelegate-mda.md)|[contextSwitchDeadlock](../../../docs/framework/debug-trace-profile/contextswitchdeadlock-mda.md)|  
|[dangerousThreadingAPI](../../../docs/framework/debug-trace-profile/dangerousthreadingapi-mda.md)|[dateTimeInvalidLocalFormat](../../../docs/framework/debug-trace-profile/datetimeinvalidlocalformat-mda.md)|  
|[dirtyCastAndCallOnInterface](../../../docs/framework/debug-trace-profile/dirtycastandcalloninterface-mda.md)|[disconnectedContext](../../../docs/framework/debug-trace-profile/disconnectedcontext-mda.md)|  
|[dllMainReturnsFalse](../../../docs/framework/debug-trace-profile/dllmainreturnsfalse-mda.md)|[exceptionSwallowedOnCallFromCom](../../../docs/framework/debug-trace-profile/exceptionswallowedoncallfromcom-mda.md)|  
|[failedQI](../../../docs/framework/debug-trace-profile/failedqi-mda.md)|[fatalExecutionEngineError](../../../docs/framework/debug-trace-profile/fatalexecutionengineerror-mda.md)|  
|[gcManagedToUnmanaged](../../../docs/framework/debug-trace-profile/gcmanagedtounmanaged-mda.md)|[gcUnmanagedToManaged](../../../docs/framework/debug-trace-profile/gcunmanagedtomanaged-mda.md)|  
|[illegalPrepareConstrainedRegion](../../../docs/framework/debug-trace-profile/illegalprepareconstrainedregion-mda.md)|[invalidApartmentStateChange](../../../docs/framework/debug-trace-profile/invalidapartmentstatechange-mda.md)|  
|[invalidCERCall](../../../docs/framework/debug-trace-profile/invalidcercall-mda.md)|[invalidFunctionPointerInDelegate](../../../docs/framework/debug-trace-profile/invalidfunctionpointerindelegate-mda.md)|  
|[invalidGCHandleCookie](../../../docs/framework/debug-trace-profile/invalidgchandlecookie-mda.md)|[invalidIUnknown](../../../docs/framework/debug-trace-profile/invalidiunknown-mda.md)|  
|[invalidMemberDeclaration](../../../docs/framework/debug-trace-profile/invalidmemberdeclaration-mda.md)|[invalidOverlappedToPinvoke](../../../docs/framework/debug-trace-profile/invalidoverlappedtopinvoke-mda.md)|  
|[invalidVariant](../../../docs/framework/debug-trace-profile/invalidvariant-mda.md)|[jitCompilationStart](../../../docs/framework/debug-trace-profile/jitcompilationstart-mda.md)|  
|[loaderLock](../../../docs/framework/debug-trace-profile/loaderlock-mda.md)|[loadFromContext](../../../docs/framework/debug-trace-profile/loadfromcontext-mda.md)|  
|[marshalCleanupError](../../../docs/framework/debug-trace-profile/marshalcleanuperror-mda.md)|[marshaling](../../../docs/framework/debug-trace-profile/marshaling-mda.md)|  
|[memberInfoCacheCreation](../../../docs/framework/debug-trace-profile/memberinfocachecreation-mda.md)|[moduloObjectHashcode](../../../docs/framework/debug-trace-profile/moduloobjecthashcode-mda.md)|  
|[nonComVisibleBaseClass](../../../docs/framework/debug-trace-profile/noncomvisiblebaseclass-mda.md)|[notMarshalable](../../../docs/framework/debug-trace-profile/notmarshalable-mda.md)|  
|[openGenericCERCall](../../../docs/framework/debug-trace-profile/opengenericcercall-mda.md)|[overlappedFreeError](../../../docs/framework/debug-trace-profile/overlappedfreeerror-mda.md)|  
|[pInvokeLog](../../../docs/framework/debug-trace-profile/pinvokelog-mda.md)|[pInvokeStackImbalance](../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md)|  
|[raceOnRCWCleanup](../../../docs/framework/debug-trace-profile/raceonrcwcleanup-mda.md)|[reentrancy](../../../docs/framework/debug-trace-profile/reentrancy-mda.md)|  
|[releaseHandleFailed](../../../docs/framework/debug-trace-profile/releasehandlefailed-mda.md)|[reportAvOnComRelease](../../../docs/framework/debug-trace-profile/reportavoncomrelease-mda.md)|  
|[streamWriterBufferedDataLost](../../../docs/framework/debug-trace-profile/streamwriterbuffereddatalost-mda.md)|[virtualCERCall](../../../docs/framework/debug-trace-profile/virtualcercall-mda.md)|  
  
 既定では、.NET Framework はすべてのマネージ デバッガーに対して MDA のサブセットをアクティブにします。 Visual Studio で既定のセットを表示するには、**[デバッグ]** メニューの **[例外]** をクリックし、**[マネージ デバッグ アシスタント]** の一覧を展開します。  
  
## <a name="enabling-and-disabling-mdas"></a>MDA の有効化と無効化  
 MDA は、レジストリ キー、環境変数、およびアプリケーション構成設定を使用して有効または無効にできます。 アプリケーション構成設定を使用するには、レジストリ キーまたは環境変数を有効にする必要があります。  
  
 Visual Studio 2005 以降のバージョンでは、ホスティング プロセスが有効な場合、既定のセットに含まれている MDA を無効にしたり、既定のセットに含まれていない MDA を有効にしたりはできません。 ホスティング プロセスは既定で有効になるため、明示的に無効にする必要があります。  
  
 Visual Studio でホスティング プロセスを無効にするには、次の操作を行います。  
  
1.  **ソリューション エクスプローラー**でプロジェクトを選択します。  
  
2.  **[プロジェクト]** メニューの **[プロパティ]** をクリックします。  
  
     **[プロジェクト デザイナー]** ウィンドウが表示されます。  
  
3.  **[デバッグ]** タブをクリックします。  
  
4.  **[デバッガーを有効にする]** セクションで、**[Visual Studio ホスティング プロセスを有効にする]** チェック ボックスをオフにします。  
  
 ただし、ホスティング プロセスを無効にすると、パフォーマンスに影響する場合があります。 Visual Studio で、MDA 通知を受け取ったときに MDA ダイアログ ボックスが表示されないようにすると、MDA を無効にする必要がありません。 そのためには、**[デバッグ]** メニューの **[例外]** をクリックし、**[マネージ デバッグ アシスタント]** の一覧を展開し、個々の MDA に対して **[スローされるとき]** チェック ボックスをオフにします。  
  
### <a name="enabling-and-disabling-mdas-by-using-a-registry-key"></a>レジストリ キーを使用した MDA の有効化と無効化  
 MDA を有効にするには、Windows レジストリに HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\MDA サブキー (REG_SZ 型、値 1) を追加します。 MDAEnable.reg という名前のテキスト ファイルに次の例をコピーします。Windows レジストリ エディター (RegEdit.exe) を開き、**[ファイル]** メニューで **[インポート]** を選択します。 MDAEnable.reg ファイルを選択します。そのコンピューターで MDA が有効になります。 サブキーを (DWARD 値 1 ではなく) 文字列値 1 に設定すると、*ApplicationName.suffix*.mda.config ファイルから MDA の設定を読み取れるようになります。 (たとえばメモ帳の MDA 構成ファイルは notepad.exe.mda.config になります)  
  
```  
Windows Registry Editor Version 5.00  
  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework]  
"MDA"="1"  
```  
  
 64 ビット オペレーティング システム上で 32 ビット アプリケーションを実行しているコンピューターでは、MDA キーは次のように設定します。  
  
```  
      Windows Registry Editor Version 5.00   
  
[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework]  
"MDA"="1"  
```  
  
 詳細については、「[アプリケーション固有の構成設定を使用した MDA の有効化と無効化](#appConfig)」を参照してください。 レジストリ設定は、COMPLUS_MDA 環境変数でオーバーライドできます。 詳細については、「[環境変数を使用した MDA の有効化と無効化](#envVariable)」を参照してください。  
  
 MDA を無効にするには、Windows レジストリ エディターを使用して MDA サブキーを 0 (ゼロ) に設定します。  
  
 MDA には、レジストリ キーを追加しなくても、デバッガーにアタッチされているアプリケーションを実行すると既定で有効になるものがあります。 このようなアシスタントには、[pInvokeStackImbalance](../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md) や [invalidApartmentStateChange](../../../docs/framework/debug-trace-profile/invalidapartmentstatechange-mda.md) などがあります。 これらのアシスタントを無効にするには、このセクションの前述の説明に従って MDADisable.reg ファイルを実行します。  
  
<a name="envVariable"></a>   
### <a name="enabling-and-disabling-mdas-by-using-an-environment-variable"></a>環境変数を使用した MDA の有効化と無効化  
 MDA のアクティブ化は、COMPLUS_MDA 環境変数によって制御することもできます。この環境変数はレジストリ キーをオーバーライドします。 COMPLUS_MDA の文字列は、MDA 名やその他の特殊制御文字列の、セミコロンで区切られたリストで、大文字小文字の区別はありません。 マネージ デバッガーやアンマネージ デバッガーの下で起動すると、MDA のセットが既定で有効になります。 そのためには、デバッガーの下で既定で有効にする MDA のリスト (セミコロン区切り) を、環境変数またはレジストリ キーの値の前に暗黙的に付加します。 特殊制御文字列は次のとおりです。  
  
-   `0` - すべての MDA を非アクティブにします。  
  
-   `1` - *ApplicationName*.mda.config から MDA の設定を読み取ります。  
  
-   `managedDebugger` - デバッガーの下でマネージ実行可能ファイルを起動すると、暗黙的にアクティブ化されているすべての MDA が明示的にアクティブ化されます。  
  
-   `unmanagedDebugger` - デバッガーの下でアンマネージ実行可能ファイルを起動すると、暗黙的にアクティブ化されているすべての MDA が明示的にアクティブ化されます。  
  
 競合する設定がある場合は、最新の設定が以前の設定を次のようにオーバーライドします。  
  
-   `COMPLUS_MDA=0` は、デバッガーの下で暗黙的に有効化されている MDA を含め、すべての MDA を無効にします。  
  
-   `COMPLUS_MDA=gcUnmanagedToManaged` は、デバッガーの下で暗黙的に有効化される MDA に加えて `gcUnmanagedToManaged` も有効にします。  
  
-   `COMPLUS_MDA=0;gcUnmanagedToManaged` は `gcUnmanagedToManaged` を有効にしますが、デバッガーの下で別途暗黙的に有効化されている MDA を無効にします。  
  
<a name="appConfig"></a>   
### <a name="enabling-and-disabling-mdas-by-using-application-specific-configuration-settings"></a>アプリケーション固有の構成設定を使用した MDA の有効化と無効化  
 アプリケーションの MDA 構成ファイルでは、一部のアシスタントを個別に有効化、無効化、および構成できます。 MDA を構成する目的でアプリケーション構成ファイルの使用を有効にするには、MDA レジストリ キーまたは COMPLUS_MDA 環境変数を設定する必要があります。 アプリケーション構成ファイルは、通常、アプリケーションの実行可能ファイル (.exe) と同じディレクトリに置かれます。 このファイル名の形式は、*ApplicationName*.mda.config です (notepad.exe.mda.config など)。アプリケーション構成ファイルで有効にされたアシスタントには、そのアシスタントの動作を制御するために特別にデザインされた属性や要素が存在する場合があります。 [marshaling](../../../docs/framework/debug-trace-profile/marshaling-mda.md) を有効化して設定する方法を次の例に示します。  
  
```xml  
<mdaConfig>  
  <assistants>  
    <marshaling>  
      <methodFilter>  
        <match name="*"/>  
      </methodFilter>  
      <fieldFilter>  
        <match name="*"/>  
      </fieldFilter>  
    </marshaling>  
  </assistants>  
</mdaConfig>  
```  
  
 `Marshaling` MDA では、アプリケーションでのマネージ コードからアンマネージ コードへの遷移ごとに、アンマネージ型にマーシャリングされるマネージ型についての情報が出力されます。 また、`Marshaling` MDA では、`<methodFilter>` 子要素と `<fieldFilter>` 子要素でそれぞれ指定されたメソッドと構造体フィールドの名前をフィルター処理できます。  
  
 既定の設定を使用して複数の MDA を有効にする方法を次の例に示します。  
  
```xml  
<mdaConfig>  
  <assistants>  
    <illegalPrepareConstrainedRegion />  
    <invalidCERCall />  
    <openGenericCERCall />  
    <virtualCERCall />  
  </assistants>  
</mdaConfig>  
```  
  
> [!IMPORTANT]
>  構成ファイルに複数のアシスタントを指定する場合は、アルファベット順に記述する必要があります。 たとえば、`virtualCERCall` MDA と `invalidCERCall` MDA の両方を有効にする場合は、`<invalidCERCall />` エントリ、`<virtualCERCall />` エントリの順に追加する必要があります。 エントリがアルファベット順になっていない場合、ハンドルされない無効な構成ファイルであることを示す例外メッセージが表示されます。  
  
### <a name="mda-output"></a>MDA の出力  
 MDA の出力例を次に示します。この例は、`pInvokeStackImbalance` MDA の出力を示しています。  
  
 `A call to PInvoke function 'MDATest!MDATest.Program::StdCall' has unbalanced the stack. This is likely because the managed PInvoke signature does not match the unmanaged target signature. Check that the calling convention and parameters of the PInvoke signature match the target unmanaged signature.`  
  
## <a name="see-also"></a>関連項目  
 [デバッグ、トレース、およびプロファイリング](../../../docs/framework/debug-trace-profile/index.md)

### <a name="marshalsizeof-and-marshalptrtostructure-overloads-break-dynamic-code"></a>Marshal.SizeOf および Marshal.PtrToStructure オーバー ロードがダイナミック コードを中断する

|   |   |
|---|---|
|説明|.NET Framework 4.5.1 以降では、メソッド <xref:System.Runtime.InteropServices.Marshal.SizeOf%60%601>、<xref:System.Runtime.InteropServices.Marshal.SizeOf%60%601(%60%600)>、<xref:System.Runtime.InteropServices.Marshal.PtrToStructure(System.IntPtr,System.Object)>、<xref:System.Runtime.InteropServices.Marshal.PtrToStructure(System.IntPtr,System.Type)>、<xref:System.Runtime.InteropServices.Marshal.PtrToStructure%60%601(System.IntPtr)>、または <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%60%601(System.IntPtr,%60%600)> への動的なバインドを (たとえば、Windows PowerShell、IronPython、または C# のダイナミック キーワードを使用して) 行うと、これらのメソッドの新しいオーバーロードが追加され、スクリプト エンジンにとってあいまいなことがあるため、<code>MethodInvocationExceptions</code> になります。|
|提案される解決策|使用するオーバーロードを明確に示すように、スクリプトを更新します。 これは、一般に、メソッドの型パラメーターを <xref:System.Type> として明示的にキャストすることによって行われます。 この問題の回避方法の詳細と例については、[このリンク](https://support.microsoft.com/kb/2909958/) を参照してください。|
|スコープ|マイナー|
|Version|4.5.1|
|型|ランタイム|


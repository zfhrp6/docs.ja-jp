---
title: "方法: HRESULT に例外を割り当てる | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "COM 相互運用機能, 例外"
  - "COM 相互運用機能, HRESULT"
  - "例外, HRESULT"
  - "HRESULT"
  - "相互運用 (アンマネージ コードとの), 例外"
  - "相互運用 (アンマネージ コードとの), HRESULT"
ms.assetid: 610b364b-2761-429d-9c4a-afbc3e66f1b9
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# 方法: HRESULT に例外を割り当てる
COM のメソッドは、HRESULT を返すことによってエラーを報告します。.NET のメソッドは、例外をスローすることによってエラーを報告します。  ランタイムは、この 2 つの間の遷移を処理します。  .NET Framework のそれぞれの例外クラスが HRESULT に割り当てられます。  
  
 ユーザー定義の例外クラスは、適切な HRESULT であればどの HRESULT でも指定できます。  これらの例外クラスは、例外オブジェクトの **HResult** フィールドを設定することより、例外が生成されたときに返す HRESULT を動的に変更できます。  アンマネージ プロセスの .NET オブジェクトに実装されている **IErrorInfo** インターフェイスを通じて、クライアントに例外についての追加情報が提供されます。  
  
 **System.Exception** を拡張するクラスを作成する場合は、構築時に HRESULT フィールドを設定する必要があります。  それ以外の場合、HRESULT の値は基本クラスによって割り当てられます。  例外のコンストラクターに値を供給することにより、既存の HRESULT に新しい例外クラスを割り当てることができます。  
  
 スレッドに `IErrorInfo` がある場合、ランタイムが `HRESULT` を無視することがあることに注意してください。  この動作は、`HRESULT` と `IErrorInfo` が同じエラーを表明しない場合に発生します。   ``  
  
### 新しい例外クラスを作成し、HRESULT に割り当てるには  
  
1.  次のコードを使用し、新しい例外クラス `NoAccessException` を作成し、HRESULT `E_ACCESSDENIED` に割り当てます。  
  
    ```cpp  
    Class NoAccessException : public ApplicationException  
    {  
        NoAccessException () {  
        HResult = E_ACCESSDENIED;   
    }  
    }  
    CMyClass::MethodThatThrows  
    {  
    throw new NoAccessException();  
    }  
    ```  
  
 マネージ コードとアンマネージ コードが同時に使用されているプログラム \(任意のプログラミング言語\) もあります。  たとえば、次のコード例のカスタム マーシャラーは、**Marshal.ThrowExceptionForHR\(int HResult\)** メソッドを使用して、特定の HRESULT 値を持つ例外をスローします。  このメソッドは、HRESULT を調べ、適切な例外型を生成します。  たとえば、次のコードの HRESULT は、**ArgumentException** を生成します。  
  
```cpp  
CMyClass::MethodThatThrows  
{  
    Marshal.ThrowExceptionForHR(COR_E_ARGUMENT);  
}  
```  
  
 各 HRESULT から対応する .NET Framework の例外クラスへのすべての対応付けを次の表に示します。  
  
|HRESULT|.NET の例外|  
|-------------|--------------|  
|**MSEE\_E\_APPDOMAINUNLOADED**|**AppDomainUnloadedException**|  
|**COR\_E\_APPLICATION**|**ApplicationException**|  
|**COR\_E\_ARGUMENT または E\_INVALIDARG**|**ArgumentException**|  
|**COR\_E\_ARGUMENTOUTOFRANGE**|**ArgumentOutOfRangeException**|  
|**COR\_E\_ARITHMETIC または ERROR\_ARITHMETIC\_OVERFLOW**|**ArithmeticException**|  
|**COR\_E\_ARRAYTYPEMISMATCH**|**ArrayTypeMismatchException**|  
|**COR\_E\_BADIMAGEFORMAT または RROR\_BAD\_FORMAT**|**BadImageFormatException**|  
|**COR\_E\_COMEMULATE\_ERROR**|**COMEmulateException**|  
|**COR\_E\_CONTEXTMARSHAL**|**ContextMarshalException**|  
|**COR\_E\_CORE**|**CoreException**|  
|**NTE\_FAIL**|**CryptographicException**|  
|**COR\_E\_DIRECTORYNOTFOUND または ERROR\_PATH\_NOT\_FOUND**|**DirectoryNotFoundException**|  
|**COR\_E\_DIVIDEBYZERO**|**DivideByZeroException**|  
|**COR\_E\_DUPLICATEWAITOBJECT**|**DuplicateWaitObjectException**|  
|**COR\_E\_ENDOFSTREAM**|**EndOfStreamException**|  
|**COR\_E\_TYPELOAD**|**EntryPointNotFoundException**|  
|**COR\_E\_EXCEPTION**|**例外**|  
|**COR\_E\_EXECUTIONENGINE**|**ExecutionEngineException**|  
|**COR\_E\_FIELDACCESS**|**FieldAccessException**|  
|**COR\_E\_FILENOTFOUND または ERROR\_FILE\_NOT\_FOUND**|**FileNotFoundException**|  
|**COR\_E\_FORMAT**|**FormatException**|  
|**COR\_E\_INDEXOUTOFRANGE**|**IndexOutOfRangeException**|  
|**COR\_E\_INVALIDCAST または E\_NOINTERFACE**|**InvalidCastException**|  
|**COR\_E\_INVALIDCOMOBJECT**|**InvalidComObjectException**|  
|**COR\_E\_INVALIDFILTERCRITERIA**|**InvalidFilterCriteriaException**|  
|**COR\_E\_INVALIDOLEVARIANTTYPE**|**InvalidOleVariantTypeException**|  
|**COR\_E\_INVALIDOPERATION**|**InvalidOperationException**|  
|**COR\_E\_IO**|**IOException**|  
|**COR\_E\_MEMBERACCESS**|**AccessException**|  
|**COR\_E\_METHODACCESS**|**MethodAccessException**|  
|**COR\_E\_MISSINGFIELD**|**MissingFieldException**|  
|**COR\_E\_MISSINGMANIFESTRESOURCE**|**MissingManifestResourceException**|  
|**COR\_E\_MISSINGMEMBER**|**MissingMemberException**|  
|**COR\_E\_MISSINGMETHOD**|**MissingMethodException**|  
|**COR\_E\_MULTICASTNOTSUPPORTED**|**MulticastNotSupportedException**|  
|**COR\_E\_NOTFINITENUMBER**|**NotFiniteNumberException**|  
|**E\_NOTIMPL**|**NotImplementedException**|  
|**COR\_E\_NOTSUPPORTED**|**NotSupportedException**|  
|**COR\_E\_NULLREFERENCE または E\_POINTER**|**NullReferenceException**|  
|**COR\_E\_OUTOFMEMORY または**<br /><br /> **E\_OUTOFMEMORY**|**OutOfMemoryException**|  
|**COR\_E\_OVERFLOW**|**OverflowException**|  
|**COR\_E\_PATHTOOLONG または ERROR\_FILENAME\_EXCED\_RANGE**|**PathTooLongException**|  
|**COR\_E\_RANK**|**RankException**|  
|**COR\_E\_REFLECTIONTYPELOAD**|**ReflectionTypeLoadException**|  
|**COR\_E\_REMOTING**|**RemotingException**|  
|**COR\_E\_SAFEARRAYTYPEMISMATCH**|**SafeArrayTypeMismatchException**|  
|**COR\_E\_SECURITY**|**SecurityException**|  
|**COR\_E\_SERIALIZATION**|**SerializationException**|  
|**COR\_E\_STACKOVERFLOW または ERROR\_STACK\_OVERFLOW**|**StackOverflowException**|  
|**COR\_E\_SYNCHRONIZATIONLOCK**|**SynchronizationLockException**|  
|**COR\_E\_SYSTEM**|**SystemException**|  
|**COR\_E\_TARGET**|**TargetException**|  
|**COR\_E\_TARGETINVOCATION**|**TargetInvocationException**|  
|**COR\_E\_TARGETPARAMCOUNT**|**TargetParameterCountException**|  
|**COR\_E\_THREADABORTED**|**ThreadAbortException**|  
|**COR\_E\_THREADINTERRUPTED**|**ThreadInterruptedException**|  
|**COR\_E\_THREADSTATE**|**ThreadStateException**|  
|**COR\_E\_THREADSTOP**|**ThreadStopException**|  
|**COR\_E\_TYPELOAD**|**TypeLoadException**|  
|**COR\_E\_TYPEINITIALIZATION**|**TypeInitializationException**|  
|**COR\_E\_VERIFICATION**|**VerificationException**|  
|**COR\_E\_WEAKREFERENCE**|**WeakReferenceException**|  
|**COR\_E\_VTABLECALLSNOTSUPPORTED**|**VTableCallsNotSupportedException**|  
|**上記以外のすべての HRESULT**|**COMException**|  
  
 拡張されたエラー情報を取得するために、マネージ クライアントは、生成された例外オブジェクトの各フィールドを調べます。  例外オブジェクトでエラーについての有益な情報を提供できるようにするには、COM オブジェクトは、**IErrorInfo** インターフェイスを実装している必要があります。  ランタイムは、**IErrorInfo** によって提供される情報を使用して、例外オブジェクトを初期化します。  
  
 COM オブジェクトが **IErrorInfo** をサポートしていない場合、ランタイムは既定の値を使用して例外オブジェクトを初期化します。  次の表で、例外オブジェクトに関連付けられた各フィールドを一覧し、COM オブジェクトが **IErrorInfo** をサポートしている場合の既定の情報ソースを示します。  
  
 スレッドに `IErrorInfo` がある場合、ランタイムが `HRESULT` を無視することがあることに注意してください。  この動作は、`HRESULT` と `IErrorInfo` が同じエラーを表明しない場合に発生します。   ``  
  
|例外フィールド|COM からの情報のソース|  
|-------------|-------------------|  
|**ErrorCode**|呼び出しから返された HRESULT。|  
|**HelpLink**|**IErrorInfo\-\>HelpContext** が 0 \(ゼロ\) 以外の場合は、文字列は **IErrorInfo\-\>GetHelpFile** と "\#" と **IErrorInfo\-\>GetHelpContext** を連結して構成されます。  それ以外の場合は、文字列は、**IErrorInfo\-\>GetHelpFile** から返されます。|  
|**InnerException**|常に null 参照 \(Visual Basic では **Nothing**\)。|  
|**Message**|**IErrorInfo\-\>GetDescription** から返された文字列。|  
|**ソース**|**IErrorInfo\-\>GetSource** から返された文字列。|  
|**StackTrace**|スタック トレース。|  
|**TargetSite**|失敗し、HRESULT を返したメソッドの名前。|  
  
 **Message**、**Source**、**StackTrace** の各例外フィールドは、**StackOverflowException** では使用できません。  
  
## 参照  
 [Advanced COM Interoperability](http://msdn.microsoft.com/ja-jp/3ada36e5-2390-4d70-b490-6ad8de92f2fb)   
 [例外](../../../docs/standard/exceptions/index.md)
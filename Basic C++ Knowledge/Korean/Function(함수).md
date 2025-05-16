<h1 style="min-height: 1em; margin: 0; padding: 0; font-family: Helvetica, Arial, sans-serif; line-height: 1.0;">함수 (Function)</h1>
<h2 style="min-height: 1em; margin: 0; padding: 0; font-family: Helvetica, Arial, sans-serif; line-height: 1.0;">1. 함수란 무엇이며, 왜 필요한가?</h2>
<blockquote style="font-family: Helvetica, Arial, sans-serif; line-height: 1.0; margin: 0; padding: 0; border-left: 5px solid #ccc; background-color: #f8f8f8; position: relative; z-index: 1; min-height: 1em;">
<div style="min-height: 1em; margin: 0; padding: 0; font-family: Helvetica, Arial, sans-serif; font-size: 16px; line-height: 1.0;"><em style="min-height: 1em; margin: 0; padding: 0; font-family: Helvetica, Arial, sans-serif; line-height: 1.0;">"함수는 작은 프로그램이다. 큰 문제를 작은 문제로 나누는 가장 좋은 방법이다."<br style="min-height: 1em; margin: 0; padding: 0; font-family: Helvetica, Arial, sans-serif; line-height: 1.0;"></em></div>
<div style="min-height: 1em; margin: 0; padding: 0; font-family: Helvetica, Arial, sans-serif; font-size: 16px; line-height: 1.0; text-align: right;"><em style="min-height: 1em; margin: 0; padding: 0; font-family: Helvetica, Arial, sans-serif; line-height: 1.0;">&mdash; 로버트 C. 마틴(Robert C. Martin), 『클린 코드』<br style="min-height: 1em; margin: 0; padding: 0; font-family: Helvetica, Arial, sans-serif; line-height: 1.0;"></em>
<div style="min-height: 1em; margin: 0; padding: 0; font-family: Helvetica, Arial, sans-serif; font-size: 16px; line-height: 1.0; text-align: left;"><em style="min-height: 1em; margin: 0; padding: 0; font-family: Helvetica, Arial, sans-serif; line-height: 1.0;">"짧은 함수는 작은 이야기를 말하고, 그 이야기는 이름으로 잘 나타나야 한다."</em></div>
<div style="min-height: 1em; margin: 0; padding: 0; font-family: Helvetica, Arial, sans-serif; font-size: 16px; line-height: 1.0;"><em style="min-height: 1em; margin: 0; padding: 0; font-family: Helvetica, Arial, sans-serif; line-height: 1.0;">&mdash; 켄트 벡(Kent Beck), 『테스트 주도 개발(TDD)』</em><span style="min-height: 1em; margin: 0; padding: 0; font-family: Helvetica, Arial, sans-serif; line-height: 1.0; text-align: left;">​</span></div>
</div>
</blockquote>
<div style="min-height: 1em; margin: 0; padding: 0; font-family: Helvetica, Arial, sans-serif; font-size: 16px; line-height: 1.0;">함수란 특정 동작을 수행하는 일련의 코드들을 한 묶음으로 만들어 놓은 것을 의미합니다. 만약 함수라는 것이 존재치 않는다면, 특정 동작을 하기 위한 코드들을 매 호출마다 하나씩 직접 넣어야 했을 것이고, 소스 코드의 길이는 엄청나게 늘어났을 것입니다. 더불어, 동작을 실행중인 코드의 일부분이 잘못되는 등의 오류를 발견해서 수정하면, 엄청나게 커진 소스코드에서 똑같은 동작을 하는 부분을 하나씩 찾아서 전부 고쳐줘야만 올바르게 프로그램이 동작할 겁니다. 생각만 해도 머리가 아프고, 굉장히 시간이 많이 걸리는 작업이라는 생각이 들지 않나요? 하지만 함수를 사용하면 이 모든 문제를 해결할 수 있습니다. A라는 동작을 수행하는 함수를 만든다면, 매번 A의 전체 코드가 들어갈 자리에 해당 함수를 호출하기만 하면 됩니다. 더불어, 함수는 이름을 설정할 수 있기 때문에, 더 이상 A를 수행하는 코드들을 보면서 어디까지가 A라는 동작을 수행하는지를 확인할 필요도 없습니다. A()라는 함수를 호출함으로써 우리는 그 함수가 A라는 동작을 수행하는 함수라는 것을 알 수 있습니다. 실제 코드로 예제를 들어 볼까요?</div>
<div style="min-height: 1em; margin: 0; padding: 0; font-family: Helvetica, Arial, sans-serif; font-size: 16px; line-height: 1.0;">
<pre class="language-cpp" style="min-height: 1em; margin: 0; padding: 0; font-family: Helvetica, Arial, sans-serif; line-height: 1.0;"><code style="min-height: 1em; margin: 0; padding: 0; font-family: Helvetica, Arial, sans-serif; line-height: 1.0;">#include &lt;iostream&gt;
using namespace std;

int main() {
    // 첫 번째 별 10개 출력
    for (int i = 0; i &lt; 10; i++) {
        cout &lt;&lt; "*";
    }
    cout &lt;&lt; endl;

    // 두 번째 별 10개 출력
    for (int i = 0; i &lt; 10; i++) {
        cout &lt;&lt; "*";
    }
    cout &lt;&lt; endl;

    // 세 번째 별 10개 출력
    for (int i = 0; i &lt; 10; i++) {
        cout &lt;&lt; "*";
    }
    cout &lt;&lt; endl;

    return 0;
}</code></pre>
</div>
<div style="min-height: 1em; margin: 0; padding: 0; font-family: Helvetica, Arial, sans-serif; font-size: 16px; line-height: 1.0;">별을 10개 출력하는 동작만을 수행하는 코드입니다. 동일한 코드가 세 번이나 반복되고 있지요. 만약 동작이 단순히 별을 찍는 것이 아니라, 매우 복잡한 일련의 과정을 걸쳐야 한다면 소스코드는 엄청나게 길어지고, 어느 한 부분을 수정해야 한다면 해당 로직을 쓰는 모든 부분을 수정해야 할 겁니다. 그렇다면 함수를 쓴 코드는 어떨까요? 바로 아래는 별을 찍는 동작을 수행하는 함수를 정의하고, 해당 함수를 사용한 코드입니다.</div>
<pre class="language-cpp" style="min-height: 1em; margin: 0; padding: 0; font-family: Helvetica, Arial, sans-serif; line-height: 1.0;"><code style="min-height: 1em; margin: 0; padding: 0; font-family: Helvetica, Arial, sans-serif; line-height: 1.0;">#include &lt;iostream&gt;
using namespace std;

// 별 10개를 출력하는 함수
void printStars() {
    for (int i = 0; i &lt; 10; i++) {
        cout &lt;&lt; "*";
    }
    cout &lt;&lt; endl;
}

int main() {
    printStars();  // 첫 번째
    printStars();  // 두 번째
    printStars();  // 세 번째

    return 0;
}</code></pre>
<div style="min-height: 1em; margin: 0; padding: 0; font-family: Helvetica, Arial, sans-serif; font-size: 16px; line-height: 1.0;">코드가 매우 간결해졌습니다. 더불어서, 이제 별을 찍는 함수를 수정하고 싶으면 <code style="min-height: 1em; margin: 0; padding: 0; font-family: Helvetica, Arial, sans-serif; line-height: 1.0;">printStars()</code>함수만 수정하면 공통적으로 모두 적용 됩니다.</div>
<h2 style="min-height: 1em; margin: 0; padding: 0; font-family: Helvetica, Arial, sans-serif; line-height: 1.0;">2. UE4SS C++ Modding에서의 함수</h2>
<div style="min-height: 1em; margin: 0; padding: 0; font-family: Helvetica, Arial, sans-serif; font-size: 16px; line-height: 1.0;">간단하게 함수란 무엇을 의미하며, 사용하면 어떤 이점이 있는지 살펴 보았습니다. 중요한 부분은 <strong style="min-height: 1em; margin: 0; padding: 0; font-family: Helvetica, Arial, sans-serif; line-height: 1.0;">함수는 특정 동작을 수행하는 일련의 코드 묶음</strong>이라는 점입니다. 다시 말하면, 해당 함수를 호출할 수 있다면 특정 동작을 수행할 수 있다는 말과 같습니다. 모딩을 하려는 게임 내에도 수많은 함수들이 있습니다. 우리가 원하는 특정한 동작을 구현하려면, 궁극적으로는 이미 구현되어 있는 함수들을 조합해야 하고, 특정 동작 도중에 무언가 처리를 하고 싶다면 역시 해당 동작을 수행하는 함수를 Hooking 해야 합니다. 일단 가장 먼저 함수를 후킹하는 방법에 대해서 알아보겠씁니다.</div>
<h3 style="min-height: 1em; margin: 0; padding: 0; font-family: Helvetica, Arial, sans-serif; line-height: 1.0;">2.1 UE4SS C++ Modding에서 함수를 후킹하는 방법</h3>
<div style="min-height: 1em; margin: 0; padding: 0; font-family: Helvetica, Arial, sans-serif; font-size: 16px; line-height: 1.0;">함수를 후킹하는 코드는 아래와 같은 형식을 따릅니다.</div>
<div style="min-height: 1em; margin: 0; padding: 0; font-family: Helvetica, Arial, sans-serif; font-size: 16px; line-height: 1.0;">
<pre class="language-cpp" style="min-height: 1em; margin: 0; padding: 0; font-family: Helvetica, Arial, sans-serif; line-height: 1.0;"><code style="min-height: 1em; margin: 0; padding: 0; font-family: Helvetica, Arial, sans-serif; line-height: 1.0;">RC::Unreal::UFunction* ClientRestartFunction = Unreal::UObjectGlobals::StaticFindObject&lt;Unreal::UFunction*&gt;(nullptr, nullptr, STR("/Script/Engine.PlayerController:ClientRestart"));
ClientRestartFunction-&gt;RegisterPostHook([this](RC::Unreal::UnrealScriptFunctionCallableContext&amp; Context, void* customData) {
        // Function Codes
        });</code></pre>
</div>
<div style="min-height: 1em; margin: 0; padding: 0; font-family: Helvetica, Arial, sans-serif; font-size: 16px; line-height: 1.0;">코드를 천천히 살펴보도록 합시다. 먼저, Unreal Engine에서 함수들은 UFunction 이라는 타입으로 관리됩니다. 어떻게 함수가 타입으로 관리될 수 있을까요? 함수의 식별자는 사실 메모리 상에서의 실행 코드들의 시작 주소를 가리킬 뿐입니다. 따라서 우리는 함수를 하나의 포인터로 취급할 수 있습니다(더 자세한 정보를 원하시면 함수 포인터(Function Pointer)를 검색해 보세요!). 처음에 StaticFIndObject를 통해서 찾고자 하는 함수를 가져옵니다. 찾고자 하는 함수는 경로로 표시됩니다. UE4SS에서 dump를 생성하면 각 Function들의 경로를 확인할 수 있습니다. 이렇게 가져올 때에는, UFunction*로 가져옵니다.</div>
<div style="min-height: 1em; margin: 0; padding: 0; font-family: Helvetica, Arial, sans-serif; font-size: 16px; line-height: 1.0;">UFunction*를 가져왔다면 이제 함수 객체에 대해서 <code style="min-height: 1em; margin: 0; padding: 0; font-family: Helvetica, Arial, sans-serif; line-height: 1.0;">RegisterPostHook</code>또는 <code style="min-height: 1em; margin: 0; padding: 0; font-family: Helvetica, Arial, sans-serif; line-height: 1.0;">RegisterPreHook</code>을 이용해서 함수 실행 후와 전에 각각 실행할 동작을 정할 수 있습니다. 두 함수는 모두 동일한 파라미터인 <code style="min-height: 1em; margin: 0; padding: 0; font-family: Helvetica, Arial, sans-serif; line-height: 1.0;">UnrealScriptFunctionCallableContext</code>타입의 매개변수와, <code style="min-height: 1em; margin: 0; padding: 0; font-family: Helvetica, Arial, sans-serif; line-height: 1.0;">customData</code>라는 매개변수를 받습니다. 우리가 주목할 부분은 <code style="min-height: 1em; margin: 0; padding: 0; font-family: Helvetica, Arial, sans-serif; line-height: 1.0;">Context</code>매개 변수입니다. Context 매개변수를 이용하면 함수의 파라미터와 반환값 까지도 읽어낼 수 있습니다. 위 과정을 따르면 함수를 성공적으로 후킹할 수 있습니다. 더불어서, 함수를 실행시킨 인스턴스의 정보 또한 Context를 가져올 수 있습니다!</div>
<h3 style="min-height: 1em; margin: 0; padding: 0; font-family: Helvetica, Arial, sans-serif; font-size: 16px; line-height: 1.0;">2.2 UE4SS C++ Modding에서 게임의 함수를 호출하는 방법</h3>
<div style="min-height: 1em; margin: 0; padding: 0; font-family: Helvetica, Arial, sans-serif; font-size: 16px; line-height: 1.0;">함수를 후킹하는 것과 달리, 함수를 호출하고 반환값이나 파라미터등을 받아오는 방법은 조금 더 까다롭습니다. 함수를 호출하는 것의 핵심은 <strong style="min-height: 1em; margin: 0; padding: 0; font-family: Helvetica, Arial, sans-serif; line-height: 1.0;">메모리 레이아웃</strong>과 <strong style="min-height: 1em; margin: 0; padding: 0; font-family: Helvetica, Arial, sans-serif; line-height: 1.0;">메모리 할당</strong>, 그리고 <strong style="min-height: 1em; margin: 0; padding: 0; font-family: Helvetica, Arial, sans-serif; line-height: 1.0;">구조체와 포인터</strong>입니다. 아래는 제가 작성한 UFunction 호출 함수입니다. 함께 코드를 살펴보면서 어떻게 해야 게임의 함수를 호출할 수 있는지 확인ㅇ해 보도록 할까요?</div>
<div style="min-height: 1em; margin: 0; padding: 0; font-family: Helvetica, Arial, sans-serif; font-size: 16px; line-height: 1.0;">
<pre class="language-cpp" style="min-height: 1em; margin: 0; padding: 0; font-family: Helvetica, Arial, sans-serif; line-height: 1.0;"><code style="min-height: 1em; margin: 0; padding: 0; font-family: Helvetica, Arial, sans-serif; line-height: 1.0;">void CallUFunction(UObject* TargetObject, const std::wstring_view FunctionPath, size_t ReturnTypeSize, void* OutReturnValue, void* ParamData = nullptr)
    {
        if (!TargetObject)
        {
            // Output::send&lt;LogLevel::Verbose&gt;(STR("TargetObject is nullptr\n"));
            return;
        }

        uint8* AllocatedParamData = nullptr;

        try
        {
            // UFunction 찾기
            auto Function = UObjectGlobals::StaticFindObject&lt;UFunction*&gt;(nullptr, nullptr, FunctionPath);
            if (!Function)
            {
                // Output::send&lt;LogLevel::Verbose&gt;(STR("Function is nullptr\n"));
                return;
            }

            // 파라미터 데이터가 없으면 새로 할당
            const auto ParamStructSize = Function-&gt;GetParmsSize();

            if (!ParamData &amp;&amp; ParamStructSize &gt; 0)
            {
                AllocatedParamData = static_cast&lt;uint8*&gt;(FMemory::Malloc(ParamStructSize));
                FMemory::Memzero(AllocatedParamData, ParamStructSize);
                ParamData = AllocatedParamData;
            }

            // ProcessEvent를 통해 함수 실행
            TargetObject-&gt;ProcessEvent(Function, ParamData);

            // 반환값이 있을 경우 복사
            if (ReturnTypeSize &gt; 0 &amp;&amp; OutReturnValue != nullptr &amp;&amp; ParamData != nullptr)
            {
                const FProperty* ReturnProperty = Function-&gt;GetReturnProperty();
                if (!ReturnProperty)
                {
                    throw std::runtime_error("ReturnProperty is nullptr");
                }

                const void* RetValue = &amp;reinterpret_cast&lt;uint8*&gt;(ParamData)[ReturnProperty-&gt;GetOffset_Internal()];
                std::memcpy(OutReturnValue, RetValue, ReturnTypeSize);
            }

            if (AllocatedParamData)
            {
                FMemory::Free(AllocatedParamData);
            }
        }
        catch (const std::exception&amp; e)
        {
            printf(e.what());
            // Output::send&lt;LogLevel::Error&gt;(STR("Error during UFunction call:\n"));
            if (AllocatedParamData)
            {
                FMemory::Free(AllocatedParamData);
            }
        }
        catch (...)
        {
            // Output::send&lt;LogLevel::Error&gt;(STR("Unknown error during UFunction call\n"));
            if (AllocatedParamData)
            {
                FMemory::Free(AllocatedParamData);
            }
        }
    }

    void CallUFunction(UObject* TargetObject, UFunction* Function, size_t ReturnTypeSize, void* OutReturnValue, void* ParamData = nullptr)
    {
        if (!TargetObject)
        {
            // Output::send&lt;LogLevel::Verbose&gt;(STR("TargetObject is nullptr\n"));
            return;
        }

        if (!Function)
        {
            // Output::send&lt;LogLevel::Verbose&gt;(STR("Function is nullptr\n"));
            return;
        }

        uint8* AllocatedParamData = nullptr;

        try
        {
            const int32 ParamStructSize = Function-&gt;GetParmsSize();

            // 파라미터 데이터가 없으면 메모리 할당
            if (!ParamData &amp;&amp; ParamStructSize &gt; 0)
            {
                AllocatedParamData = static_cast&lt;uint8*&gt;(FMemory::Malloc(ParamStructSize));
                FMemory::Memzero(AllocatedParamData, ParamStructSize);
                ParamData = AllocatedParamData;
            }

            // ProcessEvent 호출
            TargetObject-&gt;ProcessEvent(Function, ParamData);

            // 반환값 처리 (필요한 경우)
            if (ReturnTypeSize &gt; 0 &amp;&amp; OutReturnValue != nullptr &amp;&amp; ParamData != nullptr)
            {
                const FProperty* ReturnProperty = Function-&gt;GetReturnProperty();
                if (!ReturnProperty)
                {
                    // Output::send&lt;LogLevel::Error&gt;(STR("ReturnProperty is nullptr\n"));
                    throw std::runtime_error("ReturnProperty is nullptr");
                }

                const uint8* RetValue = static_cast&lt;const uint8*&gt;(ParamData) + ReturnProperty-&gt;GetOffset_Internal();
                FMemory::Memcpy(OutReturnValue, RetValue, ReturnTypeSize);
            }

            if (AllocatedParamData)
            {
                FMemory::Free(AllocatedParamData);
            }
        }
        catch (const std::exception&amp; e)
        {
            printf(e.what());
            // Output::send&lt;LogLevel::Error&gt;(STR("Error during UFunction call: {}\n"));
            if (AllocatedParamData)
            {
                FMemory::Free(AllocatedParamData);
            }
        }
        catch (...)
        {
            // Output::send&lt;LogLevel::Error&gt;(STR("Unknown error during UFunction call\n"));
            if (AllocatedParamData)
            {
                FMemory::Free(AllocatedParamData);
            }
        }
    }</code></pre>
</div>
<div style="min-height: 1em; margin: 0; padding: 0; font-family: Helvetica, Arial, sans-serif; font-size: 16px; line-height: 1.0;">두 가지 버전이 있지만, 본질적으로는 동일합니다. 여기서는 두 번째 CallUFuction만을 설명하겠습니다.</div>
<div style="min-height: 1em; margin: 0; padding: 0; font-family: Helvetica, Arial, sans-serif; font-size: 16px; line-height: 1.0;">먼저 파라미터를 살펴보면, UObject 형식의 TargetObject 변수를 받고 있습니다. 이 변수는 바로 다음 파라미터인 Function 파라미터가 실행될 객체를 의미합니다. 예를 들어, <code style="min-height: 1em; margin: 0; padding: 0; font-family: Helvetica, Arial, sans-serif; line-height: 1.0;">A::SomeFunction()</code>이라는 함수가 있다면, TargetObject는 A 객체를 가리키는 포인터가, Function 파라미터에는 SomeFunction이라는 함수를 가리키는 UFunction 포인터가 들어가야 합니다. static 클래스의 함수라면 Object도 <code style="min-height: 1em; margin: 0; padding: 0; font-family: Helvetica, Arial, sans-serif; line-height: 1.0;">UObjectGlobals::StaticFindObject</code>로 찾은 오브젝트를 넣어줘야 합니다. 다음 파라미터는 함수의 반환값의 크기이고, 그 다음인 OutReturnValue는 함수 반환값이 차지하는 메모리 공간의 시작주소를 가리키는 포인터입니다. 마지막으로 ParamData가 있습니다. 만약 함수의 Param이 없다면 nullptr로 두면 됩니다. OutReturnValue와 ParamData는 어떤 형식이 들어갈 지 알 수 없기 떄문에 모든 데이터형식의 시작 주소를 가리키는 void 포인터로 선언되어 있습니다.</div>
<div style="min-height: 1em; margin: 0; padding: 0; font-family: Helvetica, Arial, sans-serif; font-size: 16px; line-height: 1.0;">그렇다면 이제 내부 로직을 천천히 살펴보도록 합시다. 먼저, 함수르 실행할 객체나 함수 그 자체가 nullptr인 경우에는 즉시 함수를 종료합니다. 만약 두 가지 다 nullptr가 아닌 유효한 데이터라면, try-catch문 내부로 진입합니다. 진입 한 뒤에는 가장 먼저 UFunction 객체로부터 파라미터 구조체의 크기를 가져옵니다. 파라미터 구조체의 크기가 0 초과이고(다시 말해서, 파라미터를 받아야 하는 함수라면) 파라미터 데이터가 nullptr라면, 메모리 레이아웃을 맞추기 위해서 파라미터 구조체를 만들고, 메모리를 할당합니다. 이미 주어진 파라미터 데이터가 있다면 별도로 할당하지 않습니다. 이후 TargetObject에서 Function을 실행하도록 합니다(<code style="min-height: 1em; margin: 0; padding: 0; font-family: Helvetica, Arial, sans-serif; line-height: 1.0;">ProcessEvent</code>).</div>

⚠ Важно, этот наброс еще не обкатан, с осторожностью используйте его в продакшене (а лучше вообще не используйте)!
Не показывайте детям, впечатлительным людям, больным эпилепсией, кормящим матерям и беременным женщинам.

# Еще один наброс на автоотписки 😅
`untilDestroyed(this)`- просто бери и пользуйся, никакого бойлерплейта и ограничений 🐱‍🏍.

На самом деле нет, ввиду подкапотной специфики angular'a, с сервисами он требует `UntilDestroy` декоратора, но, опустим эту частность)

## Зачем ты это сделал?
Да, есть минимум пяток хороших реализацией, и еще каждый наворачивает свои собственные. Но, каждая из реализаций говорит: возьми декоратор и\или имплементируй интерфейс, и это вот все еще не безопасно в плане типизации: ты должен держать в голове то, что нужно декоратор поставить, стрим обьявить, дать ему правильный тип (самостоятельно). Если же речь о декораторе на свойстве класса, то тип ты опять же ставишь самостоятельно. Другими словами - много что нужно держать в голове и не ошибаться.

Надоело, хочется по-человечески: нужен оператор, использую оператор, все остальное - долнжо как-то само магически отруливаться где-то под капотом. Другими словами - хочу DX, не хочу думать. 

## Потенциальные проблемы
Проблемы могут возникнуть при мажорных обновлениях, если команда angular'а решит перелопатить реализацию рендерера (опять, но в этом случае думаю сломается большинство либ, как всегда). Либо, если уберут __ngContext__ у компонента\директивы (у сервиса к примеру они его не подмешивают в экземпляр, и эта та самая причина почему я не могу дотянуться до кишочек и зарегать ngOnDestroy в рантайме для сервиса, как я смог это сделать для компонента)

## Дизайн 
Нет никакого большого дизайна. Есть потребность, _чтобы_работало_, вот оно и работает. 

## Тесты
Автотестами ничего не покрыто. В репе лежит прилага, которая позволяет руками потестить как ведут себя сервисы компоненты и директивы и под капотом есть пару переменных, что содержат статусы. Все тестируется ручками

Если кому-то очень захочется - будут рад если покроете тестами. Тест кейсы описать помогу

```
#include <SFML/Graphics.hpp>

int main()
{
    // 1. 그래픽 창 생성: 800x600 크기의 창 생성
    sf::RenderWindow window(sf::VideoMode(800, 600), "Rainbow Triangle");

    // 2. 삼각형 도형 생성
    sf::VertexArray triangle(sf::Triangles, 3); // 삼각형 3개 꼭짓점

    // 꼭짓점 설정 (위치 + 색상)
    triangle[0].position = sf::Vector2f(400, 100); // 위쪽
    triangle[0].color = sf::Color::Red;            // 빨강

    triangle[1].position = sf::Vector2f(200, 500); // 왼쪽 아래
    triangle[1].color = sf::Color::Green;          // 초록

    triangle[2].position = sf::Vector2f(600, 500); // 오른쪽 아래
    triangle[2].color = sf::Color::Blue;           // 파랑

    // 3. 메인 이벤트 루프
    while (window.isOpen())
    {
        sf::Event event;
        while (window.pollEvent(event))
        {
            if (event.type == sf::Event::Closed)
                window.close();
        }

        // 4. 렌더링 사이클
        window.clear(sf::Color::Black);   // 창 초기화 (검은 배경)
        window.draw(triangle);            // 삼각형 그리기
        window.display();                 // 화면에 출력
    }

    return 0;
}
```

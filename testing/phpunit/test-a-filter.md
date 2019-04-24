# Test a filter

#### Basic Example

```php
class filter_xxx_testcase extends advanced_testcase {
    protected $filter;
    protected function setUp() {
        parent::setUp();
        $this->filter = new filter_xxx(context_system::instance(), array());
    }
    
    public function test_bobs() {
        $result = trim($this->filter->filter('Hey nice bobs'));
        $this->assertEquals('Hey nice ***', $result);
    }
}    
```

#### Advanced Example

@todo with @dataProvider


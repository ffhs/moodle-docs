# Course Modules $cm

#### Get a coursemodule by instance

```php
$cm = get_coursemodule_from_instance('quiz', $quiz1->id, $this->course->id);
```

#### Delete course module

```php
course_delete_module($book->cmid);
```

## Course Modules Keys:

`mdl_modules`

```php
interface mod_type_interface {
    // Module name for assignment activity in Moodle.
    const MOD_TYPE_ASSIGN = 'assign';
    // Module name for attendance in Moodle.
    const MOD_TYPE_ATTENDANCE = 'attendance';
    // Module name for book in Moodle.
    const MOD_TYPE_BOOK = 'book';
    // Module name for chat in Moodle.
    const MOD_TYPE_CHAT = 'chat';
    // Module name for choice in Moodle.
    const MOD_TYPE_CHOICE = 'choice';
    // Module name for choicegroup in Moodle.
    const MOD_TYPE_CHOICEGROUP = 'choicegroup';
    // Module name for database in Moodle.
    const MOD_TYPE_DATA = 'data';
    // Module name for feedback in Moodle.
    const MOD_TYPE_FEEDBACK = 'feedback';
    // Module name for folder in Moodle.
    const MOD_TYPE_FOLDER = 'folder';
    // Module name for forum in Moodle.
    const MOD_TYPE_FORUM = 'forum';
    // Module name for glossary in Moodle.
    const MOD_TYPE_GLOSSARY = 'glossary';
    // Module name for imscp in Moodle.
    const MOD_TYPE_IMSCP = 'imscp';
    // Module name for journal in Moodle.
    const MOD_TYPE_JOURNAL = 'journal';
    // Module name for label in Moodle.
    const MOD_TYPE_LABEL = 'label';
    // Module name for lesson in Moodle.
    const MOD_TYPE_LESSON = 'lesson';
    // Module name for lti in Moodle.
    const MOD_TYPE_LTI = 'lti';
    // Module name for page in Moodle.
    const MOD_TYPE_PAGE = 'page';
    // Module name for questionnaire in Moodle.
    const MOD_TYPE_QUESTIONNAIRE = 'questionnaire';
    // Module name for quiz in Moodle.
    const MOD_TYPE_QUIZ = 'quiz';
    // Module name for resource in Moodle.
    const MOD_TYPE_RESOURCE = 'resource';
    // Module name for url in Moodle.
    const MOD_TYPE_URL = 'url';
    // Module name for scheduler in Moodle.
    const MOD_TYPE_SCHEDULER = 'scheduler';
    // Module name for scorm in Moodle.
    const MOD_TYPE_SCORM = 'scorm';
    // Module name for survey in Moodle.
    const MOD_TYPE_SURVEY = 'survey';
    // Module name for wiki in Moodle.
    const MOD_TYPE_WIKI = 'wiki';
    // Module name for workshop in Moodle.
    const MOD_TYPE_WORKSHOP = 'workshop';
}
```




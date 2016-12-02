# GCI-Zulip-Intro-Task
First GCI task.
class CrocodileTest(ZulipTestCase):
    def test_change_bye_message(self):
        # type: () -> None
        sender = get_user_profile_by_email('othello@zulip.com')
        client = make_client(name="test suite")
        message_id = check_send_message(sender, client, "stream", ["Verona"], "Crocodile test", "bye")
        self.assertEqual(
            Message.objects.values_list("content", flat=True).get(id=message_id),
            "See you in a while :crocodile:!")

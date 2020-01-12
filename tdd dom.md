```
console.log('\n\n\n\n')
const { expect } = require('chai')
//
// eslint-disable-next-line no-unused-vars
const axios = require('axios')
const moxios = require('moxios')

const api_url = 'api/req.json' // ???
const fake_api = '../fake_api/ticket_notification_timeout.json'

const json = require(fake_api)


require('jsdom-global')(`
<!DOCTYPE html>
<div class="content_body">
    <span id="buy_ticket"></span>
    <div class="buy-tickets">
        <h1>Tickets</h1>
        <ul class="ticket-listing">
            <li>
                <div class="info">
                    <span class="title">Sunday, 1 December 2030 </span>
                    <div class="time">0:00AM</div>
                    <div class="venue">bla bla</div>
                </div>

                <div class="links">
                    <a class="event-btn buy_ticket disabled">CURRENTLY UNAVAILABLE</a>
                </div>
            </li>
        </ul>

        <div class="ticket-price">
            <strong>Ticket price</strong>
            <div class="description"><p>Standard : $20, $10, $20</p>
            </div>
        </div>
    </div>
</div>
</html>
`)


describe('ticket_notification', () => {
    moxios.install()
    moxios.stubRequest(api_url, {
        status: 200,
        response: {
            data: json,
        },
    })

    after(function() {
        moxios.uninstall()
    })

    describe('test', () => {
        it('should run', () => {
            expect(true).to.eq(true)
        })
        it('should have virtual dom', () => {
            const body = document.querySelectorAll('body')
            expect(body).to.exist
        })
    })

})
```
